{
    "title": "Upgrade Apache Cassandra to version 3.11.10",
    "linkTitle": "Upgrade Apache Cassandra to version 3.11.10",
    "weight": 30,
    "date": "2021-07-19",
    "description": "Upgrade Apache Cassandra from version 2.2.12 to version 3.11.10."
}

## Best practice

We recommend the following when upgrading your Apache Cassandra version:

* In multi-datacenter clusters, upgrade every node in one datacenter before upgrading another datacenter. Upgrade and restart the nodes one at a time. Other nodes in the cluster continue to operate at the earlier version until all nodes are upgraded.
* When upgrading a cluster on a single-datacenter or multi-datacenter setup, you must avoid any schema changes until the entire cluster has been upgraded to the same version.
* Running `nodetool repair` on a Cassandra node will affect performance on a system running live traffic. It is recommended that you perform the Cassandra upgrade in the evening or during a maintenance window when the load is minimal.

## Cassandra upgrade steps

The following steps give an example of how to upgrade Cassandra from version 2.2.12 to version 3.11.10. The upgrade is a two stage process:

1. Stage 1 - Upgrade Cassandra from version 2.2.12 to version 2.2.19.
2. Stage 2 - Upgrade Cassandra from version 2.2.19 to version 3.11.10.

### Stage 1 - Upgrade Cassandra 2.2.12 to 2.2.19

#### Step 1 - Update Cassandra's driver configuration in the Gateway

The Cassandra driver protocol version must be set to use 'V3' prior to upgrading the Cassandra cluster. Follow the following steps on each Gateway instance to configure the protocol version:

1. Create a file called jvm.xml in the following location:

    ```
    INSTALL_DIR/apigateway/groups/GROUP_ID/INSTANCE_ID/conf
    ```
2. Edit the jvm.xml file so that the contents are as follows:

    ```
    <ConfigurationFragment>
        <VMArg name="-DCASSANDRA_PROTOCOL_VERSION=3" />
    </ConfigurationFragment>
    ```
3. Restart the API Gateway.

#### Step 2 - Install Cassandra 2.2.19

1. Download Cassandra 2.2.19 (available from: <https://downloads.apache.org/cassandra/2.2.19/>).
2. Unzip the downloaded Cassandra package.

    Copy the Cassandra 2.2.19 installation directory to the target Cassandra server node in an appropriate directory e.g. /home/cassandra-2219/.

#### Step 3 - Backup Cassandra 2.2.12

1. Find your Cassandra keyspace(s) to backup.

    Using cqlsh, execute the following command:
    ```
    SELECT * from system.schema_keyspaces;
    ```
    In the following example, `xxx_group_2` and `xxx_group_3` are API Management keyspaces:

    ![API Management keyspaces](/Images/CassandraAdminGuide/cqlsh_keyspace.png)

2. Backup Cassandra using the backup tool.

    The API Gateway backup tool is located in `install_dir/apigateway/tools/apigw-backup-tool`. To get started, you must copy the `apigw-backup-tool` folder to your Cassandra node. Update the `/conf/apigw-backup-tool.ini` file to configure your backup (see [Apache Cassandra backup and restore](/docs/cass_admin/cassandra_bur/#update-your-configuration-file)).

    After the configuration is set and Cassandra is running, run the following command to validate the configuration:
    ```
    apigw-backup-tool validateConfig 
    ```

    While Cassandra is running, run the following command to create a backup in the `backup_root_dir` (as configured in the `/conf/apigw-backup-tool.ini` file) folder:
    ```
    apigw-backup-tool backup -k <keyspace name> -s <snapshot name>
    ```

3. Backup your Cassandra configuration.

    In addition to backing up your data in Apache Cassandra keyspaces, you must also back up your Apache Cassandra configuration and API Gateway configuration. You must back up the `CASSANDRA_HOME/conf` directory on the Cassandra node.

#### Step 4 - Update Cassandra configuration files

Compare the configuration in `CASSANDRA_HOME/conf` of your Cassandra 2.2.12 installation to the configuration in your Cassandra 2.2.19 installation and apply any custom changes from Cassandra 2.2.12 to the relevant configuration file in Cassandra 2.2.19.

#### Step 5 - Copy SSL certificates

If you have SSL certificates in your Cassandra 2.2.12 installation, copy them to Cassandra 2.2.19. To copy the SSL certificates, copy the following files to `CASSANDRA_HOME/conf/` of the Cassandra 2.2.19 installation:

* `CASSANDRA_HOME/conf/.truststore`
* `CASSANDRA_HOME/conf/.truststore`

#### Step 6 - Shutdown Cassandra 2.2.12 node

1. Run Cassandra's `nodetool drain` command in `CASSANDRA_HOME/bin` to clear data from the node and isolate it from the cluster.

    ```
    $./nodetool drain
    ```

2. Kill the Cassandra process

    ```
    $ps auwx | grep cassandra
    $sudo kill pid #Stop Cassandra
    ```

#### Step 7 - Copy data from Cassandra 2.2.12 to Cassandra 2.2.19

Copy the `CASSANDRA_HOME/data` directory to the corresponding directory in your Cassandra 2.2.19 directory (e.g. /home/cassandra-2219/cassandra/). The Cassandra 2.2.19 `data` directory should then have the following sub directories:

```
commitlog
data
saved_caches
```

#### Step 8 - Start Cassandra 2.2.19

Run the following command from the `bin` directory  of the Cassandra 2.2.19 installation to start the Cassndra instance:

```
$cd /home/cassandra-2219/cassandra/bin
$./cassandra

```

Note: When starting Cassandra, if the following exception occurs during the Cassandra startup process:

```
Exception (java.lang.RuntimeException) encountered during startup: A node with address <host>/<IP> already exists, cancelling join. Use cassandra.replace_address if you want to replace this node.
```

You will need to use the `nodetool removenode` command to remove the old Cassandra 2.2.12 node from the cluster before starting the new Cassandra 2.2.19. This command must be performed from a different node than the one currently being upgraded.

1. Run `nodetool status` to get the list of nodes in the cluster and their respective Cassandra Host IDs:
    ```
    $ ./nodetool status
    Datacenter: datacenter1
    =======================
    Status=Up/Down
    |/ State=Normal/Leaving/Joining/Moving
    --  Address        Load       Tokens       Owns (effective)  Host ID                               Rack
    DN  10.142.58.95   7.26 MB    256          100.0%            3c201a6f-441a-4510-93fd-53c2025073c3  rack1
    UN  10.142.58.223  1.78 MB    256          100.0%            c2361215-be9f-4e90-8b4a-73085e1b92e1  rack1
    UN  10.142.58.195  7.25 MB    256          100.0%            3e3d345f-48ce-4224-8485-aa8e3fdac632  rack1
    ```
2. Then select the `Host ID` of the down (`DN`) node and remove it from the cluster using the `nodetool removenode` command:
    ```
    $ ./nodetool removenode 3c201a6f-441a-4510-93fd-53c2025073c3
    ```

#### Step 9 - Repeat Steps 2-8 on all other Cassandra nodes in the cluster

#### Step 10 - Run nodetool repair on each Cassandra 2.2.19 node

```
$cd /home/cassandra-2219/cassandra/bin
$./nodetool repair
```

#### Step 11 - Repeat step 9-10 on any other DC, if applicable.

### Stage 1 - Upgrade Cassandra 2.2.19 to 3.11.10

#### Step 12 - Install Cassandra 3.11.10

1. Download Cassandra 3.11.10 (available from: https://downloads.apache.org/cassandra/3.11.10/ ).
2. Unzip the downloaded Cassandra package.

    Copy the Cassandra 3.11.10 installation directory to the target Cassandra server node in an appropriate directory e.g. /home/cassandra-31110/. 

#### Step 13 - Repeat steps 2-11 (upgrading from Cassandra 2.2.19 to Cassandra 3.11.10)

#### Step 14 - Run nodetool upgradesstables on Cassandra 3.11.10

```
$cd /home/cassandra-31110/cassandra/bin
$./nodetool upgradesstables
```

#### Step 15 - Update Cassandra's driver configuration in the Gateway

Follow the following steps on each Gateway instance to reconfigure the protocol version:

1. Edit the `jvm.xml` located in `INSTALL_DIR/apigateway/groups/GROUP_ID/INSTANCE_ID/conf` and remove the previously set JVM argument. This will revert the Gateway to use Cassandra's V4 protocol.

    ```
    <ConfigurationFragment>
        <VMArg name="-DCASSANDRA_PROTOCOL_VERSION=3" />
    </ConfigurationFragment>
    ```
2. Restart the API Gateway.
