---
title: API Gateway and API Manager 7.7 August 2021 Release Notes
linkTitle: API Gateway and API Manager August 2021
weight: 95
date: 2021-06-21
description: API Gateway and API Manager updates are cumulative, comprising new
  features and changes delivered in previous updates unless specifically
  indicated otherwise in the Release notes.
---
## Installation

* To **update** your API Gateway, see [Update from API Gateway One Version](/docs/apim_installation/apigw_upgrade/upgrade_steps_oneversion/).
* To **upgrade** from an older version, see [Upgrade from API Gateway 7.5.x or 7.6.x](/docs/apim_installation/apigw_upgrade/upgrade_steps_extcass/).
* For more details on supported platforms for software installation, see [System requirements](/docs/apim_installation/apigtw_install/system_requirements/).
* For a summary of the system requirements for a Docker deployment, see [Set up Docker environment](/docs/apim_installation/apigw_containers/docker_scripts_prereqs/).

### Update a container deployment

Any custom `.fed` files deployed to a container must be upgraded using [upgradeconfig](/docs/apim_installation/apigw_upgrade/upgrade_analytics#upgradeconfig-options) or [projupgrade](/docs/apim_reference/devopstools_ref#projupgrade-command-options). They must be upgraded the same way, regardless of whether they are API Manager enabled or not. The `.fed` files contain the updates for the API Manager configuration and can be used to build containers.

## New features and enhancements

The following new features and enhancements are available in this update.

### API Gateway ELK Solution

This update confirms that the ELK *(ElasticSearch/Logstash/Kibana)* solution for APIGW has been tested and is production ready.

### placeholder

placeholder

### YAML configuration store (placeholder)

placeholder

## Important changes

It is important, especially when upgrading from an earlier version, to be aware of the following changes in the behavior or operation of the product in this update, which may impact on your current installation.

### Important changes placeholder

placeholder

### Notice of schedule change for updates
<!-- _Brian Lynch to review this section, whether it's needed -->
The cadence of the updates for API Gateway, API Manager, and API Portal has changed. From the August update onwards, the update schedule follows a three months release cadency

## Deprecated features

As part of our software development life cycle we constantly review our API Management offering. In this update, the following capabilities have been deprecated:

### Deprecated changes placeholder

placeholder

### Antivirus filters
<!-- Brian Lynch to review this section, whether it's needed -->
In the [January 2020](/docs/apim_relnotes/20200130_apimgr_relnotes/) update, we announced the deprecation of all the Antivirus filters in API Gateway. This is a reminder that in August 2021 we will remove the Antivirus filters from API Gateway. So, we recommend you to use the API Gateway's ICAP capability, which allows the gateway to integrate with ICAP capable external virus scanners.

### End of Support notices

The following items are end of support (EOS):

* placeholder

### Removed features

<!-- To stay current and align our offerings with customer demand and best practices, Axway might discontinue support for some capabilities. As part of this review, the following features have been removed: -->

No capabilities have been removed in this update.

## Fixed issues

This version of API Gateway and API Manager includes:

* Fixes from all 7.5.3, 7.6.2, and 7.7 service packs released prior to this version. For details of all the service pack fixes included, see the corresponding *SP Readme* attached to each service pack on [Axway Support](https://support.axway.com).
* Fixes from all 7.7 updates released prior to this version. For details of all the update fixes included, see the corresponding [Release note](/docs/apim_relnotes/) for each 7.7 update.

### Fixed security vulnerabilities

Table

### Other fixed issues

Table

## Known issues

The following are known issues for this update.

| Internal ID | Description                                                                                                                                                        |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| RDAPI-16486 | Changes in the mapper always require a reload in the Execute Data Maps filter and once reloaded then providing values for the required parameters must be repeated |
| RDAPI-17282 | Connector for Salesforce APIs in API Manager doesn't work or is impossible to configure                                                                            |
| RDAPI-17395 | APIGW Analytics - no data in DB during DB unavailability                                                                                                           |
| RDAPI-18332 | "Try-it" for API-Method is not working                                                                                                                             |
| RDAPI-18523 | Inconsistent application search behaviour relating to application sharing                                                                                          |
| RDAPI-18601 | EMT environmentalisation issue                                                                                                                                     |
| RDAPI-18986 | projpack is unable to merge projects after projupgrade; likely due to Default APIManager policies                                                                  |
| RDAPI-18990 | "Failed to delete undefined" window pops up unexpectedly when attempting to delete application                                                                     |
| RDAPI-19217 | Inconsistency between Application Developers and Account Settings pages in Manager                                                                                 |
| RDAPI-19292 | When an APIM admin user's login name is changed, the user is directed to a blank page                                                                              |
| RDAPI-19293 | API Catalog Try It shows only the first security device of a security profile                                                                                      |
| RDAPI-19334 | Access to retired APIs is not removed from other organizations as expected                                                                                         |
| RDAPI-19436 | API approve/enable functionality for an organization does not show on application view                                                                             |
| RDAPI-19442 | Saving Mode Stuck for the Application Creation in different session                                                                                                |
| RDAPI-19601 | Sharing section of Application issue when Organization of application changed                                                                                      |
| RDAPI-19742 | API metrics ignore an API's organization                                                                                                                           |
| RDAPI-19743 | API Broker not shown in circuit path on all failures                                                                                                               |
| RDAPI-20527 | xml2json filter, unable to use xml with valid namespace syntax                                                                                                     |
| RDAPI-20593 | Issue with Authentication profiles related to permethod override                                                                                                   |
| RDAPI-20594 | When a token is revoked with an incorrect Authorization header, the response is 400 instead of 401                                                                 |
| RDAPI-20726 | How to get attribute value for apimgmt.application.id                                                                                                              |
| RDAPI-20742 | Inconsistent deletion of Environmentalized Settings                                                                                                                |
| RDAPI-20952 | NullPointerException when opening a project with dependencies                                                                                                      |
| RDAPI-21009 | Issue after updating API Manager settings through rest api if lockUserAccount is missing                                                                           |
| RDAPI-21061 | updated error message, OAS3 file import without servers section url                                                                                                |
| RDAPI-21171 | Minor UI issue affecting pagination in API keys and Oauth client credentials                                                                                       |
| RDAPI-21275 | Application default quota in days produces "Cannot instantiate API constraint" error                                                                               |
| RDAPI-21295 | XSD files are not downloaded when Use client registry is enabled                                                                                                   |
| RDAPI-21325 | Improve load time performance of the Applications screen                                                                                                           |
| RDAPI-21332 | Cassandra 2.2.12 Vulnerabilities from latest scan                                                                                                                  |
| RDAPI-21384 | Webservice (WSDL-based) responds with 500 instead of 405 when an invalid HTTP method is used                                                                       |
| RDAPI-21411 | Inconsistent treatment of multiple scopes in Oauth request                                                                                                         |
| RDAPI-21438 | Search box for Applications will not accept certain Unicode characters                                                                                             |
| RDAPI-21456 | Application export doesn't include external credential                                                                                                             |
| RDAPI-21514 | Policy shortcut chain filter corrupts priority order when altering the sequence                                                                                    |
| RDAPI-21653 | Custom Property Maximum Size                                                                                                                                       |
| RDAPI-21675 | API Gateway Manager > Messaging > {Queue}: display issue long name queue                                                                                           |
| RDAPI-21770 | Incorrect semantics of negated match types like IS_NOT in Compare Attribute filter                                                                                 |
| RDAPI-21875 | User creation failing under small load                                                                                                                             |
| RDAPI-22073 | \[CWE-502] Deserialization of Untrusted Data via Guava - Cassandra and Configurationstudio                                                                         |
| RDAPI-22147 | API Manager GUI - API sorting issue                                                                                                                                |
| RDAPI-22164 | Policy Studio UX issue, shows original, non environmentalized URL for DB                                                                                           |
| RDAPI-22197 | Report display issue                                                                                                                                               |
| RDAPI-22204 | Wrong documentation on API Manager Swagger/OAS for corsOrigins                                                                                                     |
| RDAPI-22221 | libxml Error while importing WSDL                                                                                                                                  |
| RDAPI-22331 | automated submission form protection for forgottenpassword                                                                                                         |
| RDAPI-22333 | OAS 3 import implicitly requires a "servers" object, which should not be mandatory                                                                                 |
| RDAPI-22430 | Issues removing custom policies from API Manager                                                                                                                   |
| RDAPI-22452 | On APIMgr monitoring, application id is displayed instead of application name                                                                                      |
| RDAPI-22455 | Self crosssite scripting vulnerability in API Manager                                                                                                              |
| RDAPI-22513 | Package properties not visible, PS and CS tools on Linux                                                                                                           |
| RDAPI-22671 | XPath wizard - Unexpected behavior of 'Evaluate' button                                                                                                            |
| RDAPI-22756 | No longer able to search applications by ID on API Manager 7.7                                                                                                     |
| RDAPI-22760 | setting for EMT offload of audit.log files                                                                                                                         |
| RDAPI-22764 | Slowness with APIGateway Policy Studio, Windows ver 1803 and 1809                                                                                                  |
| RDAPI-22848 | Attempting to change the API default quota produces "cannot modify default quota properties" error                                                                 |
| RDAPI-22954 | swagger imports fine, but comes out with error from catalog 2.0 link                                                                                               |
| RDAPI-22987 | APIM login endpoint stops responding when pod has been running for 30 days                                                                                         |
| RDAPI-23222 | Unable to create user as error pop up is displayed                                                                                                                 |
| RDAPI-23326 | Cassandra CVE-2020-13946                                                                                                                                           |
| RDAPI-23379 | API Catalog shows http and https base urls, customer wants only https                                                                                              |
| RDAPI-23471 | if custom API Proxy broker, customized backend service url is not kept in serviceprofiles in .dat export                                                           |
| RDAPI-23499 | Using OAuth External Attributes to send serialized objects                                                                                                         |
| RDAPI-23500 | Trial option does not work (not fixed by RDAPI-19580)                                                                                                              |
| RDAPI-23549 | No VAPI matched request after upgrade from 7.5.3 SP12 using inbound security policy                                                                                |
| RDAPI-23557 | TraceRedactor error:java.lang.RuntimeException: regex error with code: -10                                                                                         |
| RDAPI-23571 | OAuth access tokens can be refreshed even after expiration when Cassandra TTL is NULL                                                                              |
| RDAPI-23601 | add header in inbound security for frontend doesn't appear anymore in params.header                                                                                |
| RDAPI-23654 | Trace record logs passwords in plain text at DATA level                                                                                                            |
| RDAPI-23655 | When an APIM administrator changes a user's password, the user's session should be ended                                                                           |
| RDAPI-23658 | HTTP transaction blocked by Send To JMS filter when deploying configuration                                                                                        |
| RDAPI-23723 | different crash after ModSec patch                                                                                                                                 |
| RDAPI-23779 | The http.headers attribute is vulnerable to CRLF injection                                                                                                         |
| RDAPI-23786 | nov20 PS loads a *.fed (1Mb) in +5min in win10                                                                                                                     |
| RDAPI-23820 | Memory leak in customer environment                                                                                                                                |
| RDAPI-23829 | API gateway and Portal duplicates the base url in the API catalog.                                                                                                 |
| RDAPI-23841 | Deleting an Org in API Manager always throws error/exception in trace                                                                                              |
| RDAPI-23853 | Slow API Manager GUI due to large authorization table                                                                                                              |
| RDAPI-23866 | Try-It example for SOAP request missing namespaces                                                                                                                 |
| RDAPI-23913 | Analytics PDF reports missing line item results that show on UI                                                                                                    |
| RDAPI-23946 | Cassandra 2.2.x EOL 30th April 2021                                                                                                                                |
| RDAPI-23963 | POST /applications/<app_id>/apis is much slower in Mar-21 than 7.5.3                                                                                               |
| RDAPI-23965 | release connections from pool for OracleDB-API_GW connectivity                                                                                                     |
| RDAPI-23981 | SAXParseException when attempting to process an inbound WebService request                                                                                         |
| RDAPI-23984 | "Set time" control in API Monitoring does not work fully in a Chinese locale                                                                                       |
| RDAPI-24011 | PS  doesn't open Dependencies Projects using recent projects links                                                                                                 |
| RDAPI-24024 | CVE-2021-2161 / CVE-2021-2163                                                                                                                                      |
| RDAPI-24145 | CPU spikes to 100% with unresponsive host                                                                                                                          |
| RDAPI-24148 | com.vordel.coreapireg.runtime.broker.InvokableMethodParamException: Required parameter 'null' missing                                                              |
| RDAPI-24222 | \[PS] Client Access Token Store creation: "You must enter a value for 'Purge up to'"                                                                               |
| RDAPI-24226 | pop messages are retrieved by both instances in the same group                                                                                                     |
| RDAPI-24251 | Issue in API update (API livecycle)                                                                                                                                |
| RDAPI-24256 | Policy responding to OPTIONS call returns 200 instead of 403 after upgrade from 7.5.3                                                                              |
| RDAPI-24324 | Memory leak in production                                                                                                                                          |
| RDAPI-24329 | core dump with websocket                                                                                                                                           |
| RDAPI-24345 | API Manager is matching VAPI to deleted APIs to incoming requests instead of the Published API                                                                     |
| RDAPI-24359 | OCSP filter issue with intermediate certs having same cert DN                                                                                                      |
| RDAPI-24360 | XML Complexity filter with charset of cp1252 fails                                                                                                                 |
| RDAPI-24371 | policy that check the revoked certificates throws an exception after an upgrade to 77                                                                              |
| RDAPI-24383 | Try-it not working with http port in API Manager                                                                                                                   |
| RDAPI-24400 | APIM sends Hosts header with default port even when unnecessary                                                                                                    |

### Scripting filter whiteboard attributes not preloaded for Jython scripts

The Scripting filter now uses a Jython 2.7 scripting environment (previously, Jython 2.5) to execute Jython scripts. As a result of this version change, the whiteboard attributes, such as `http.request.uri` and `http.request.verb`, are no longer preloaded for use by Jython scripts. However, you can run a Jython script to load these attributes before they are accessed as follows:

```
from com.vordel.trace import Trace

def invoke(msg):
    msg.forceGenerateAttributes()
    Trace.info("This trace statement was generated in script filter!  [" + str(msg.get("http.request.verb")) + "] [" + str(msg.get("http.request.uri")) + "]")
    return True
```

Related Issue: RDAPI-21363

### When an API Gateway instance is started, Xerces SAXParserImpl writes warnings to the error console

At API Gateway instance startup, the following warnings are logged to the error console, as opposed to the trace log:

```
Warning: org.apache.xerces.jaxp.SAXParserImpl$JAXPSAXParser: Property 'http://javax.xml.XMLConstants/property/accessExternalDTD' is not recognized.
Warning: org.apache.xerces.jaxp.SAXParserImpl$JAXPSAXParser: Property 'http://www.oracle.com/xml/jaxp/properties/entityExpansionLimit' is not recognized.
```

These new properties were added in JAXP 1.5 specification, which is supported by the embedded implementation in the JRE but not supported yet in Xerces-J Apache implementation. These are harmless warning messages, which are written to the error console instead of throwing an exception if a property is not supported by the Apache Xerces-J implementation.

Related Issue: RDAPI-22218

### No VAPI matched request after upgrade from 7.5.3 SP12 using inbound security policy

If the following errors are present in the API Gateway traces when the instance is started, then there is a duplicate remote host configuration in API Gateway and API Manager configurations.

Duplicate remote host error:

```
ERROR 11/Mar/2021:11:10:27.207 [6dc4:000000000000000000000000] Failed to configure module:
...
com.vordel.api.common.ForbiddenException: PolicyStudio-registered remote host with name 'backend' and port '8080' already exists
 at com.vordel.apiportal.api.portal.controller.RemoteHostController.checkRemoteHost(RemoteHostController.java:616)
 at com.vordel.apiportal.api.portal.controller.RemoteHostController.updateRemoteHost(RemoteHostController.java:188)
 at com.vordel.apiportal.config.PortalConfiguration.addRemoteHosts(PortalConfiguration.java:354)
 at com.vordel.apiportal.config.PortalConfiguration.configure(PortalConfiguration.java:295)
```

Failure to configure circuit for VAPI error:

```
ERROR 11/Mar/2021:11:21:11.096 [6fb9:000000000000000000000000] Error configuring circuit for Front End (Proxy) API called [AA Petstore], Version [1.0.5], Organization [c33c32c5-f32e-4e38-8c52-1f149b7ebe9d]
ERROR 11/Mar/2021:11:21:11.096 [6fb9:000000000000000000000000] Error processing VAPI change event EventTimestamp [entityType=VIRTUALIZED_API, entityId=da281a2f-4e4d-4ce0-8747-a17614978a7f, eventType=CREATEUPDATE]:
java.lang.NullPointerException
 at com.vordel.apiportal.runtime.AuthenticationPolicySecurityDevice.exists(AuthenticationPolicySecurityDevice.java:182)
 at com.vordel.apiportal.runtime.AuthenticationPolicySecurityDevice.configure(AuthenticationPolicySecurityDevice.java:73)
```

To circumvent this problem, edit the API Gateway server configuration using Policy Studio and remove the duplicate remote host definition from **Environment Configuration > Listeners**, then deploy the updated configuration back to the server or servers in a group.

Related Issue: RDAPI-23549

## Documentation

<!-- This section describes documentation enhancements and related documentation.

### Documentation enhancements -->

There are no major changes in this update.

### Related documentation

To find all available documentation for this product version:

1. Go to [Manuals on the Axway Documentation portal](https://docs.axway.com/bundle).
2. In the left pane Filters list, select your product or product version.

Customers with active support contracts need to log in to access restricted content.

For information on the different operating systems, databases, browsers, and thick client platforms supported by each Axway product, see [Supported Platforms](https://docs.axway.com/bundle/Axway_Products_SupportedPlatforms_allOS_en).

## Support services

The Axway Global Support team provides worldwide 24 x 7 support for customers with active support agreements.

Email [support@axway.com](mailto:support@axway.com) or visit [Axway Support](https://support.axway.com/).

See [Get help with API Gateway](/docs/apim_administration/apigtw_admin/trblshoot_get_help/) for the information that you should be prepared to provide when you contact Axway Support.
