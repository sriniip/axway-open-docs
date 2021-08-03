---
title: Amplify Central July 2021 Release Notes
linkTitle: Amplify Central July 2021
weight: 90
date: 2021-07-26
description: Amplify Central enables the user to manage their provider /
  consumer view. For more information, see the Amplify Central documentation.
---

## New features and enhancements

The following new features and enhancements are available in this update.

### Axway CLI / Axway Central CLI

The Axway CLI is a package for managing Amplify resources with a DevOps approach to API Management.

**Axway CLI** version 2.2.0 has been released on NPM (<https://www.npmjs.com/package/axway/v/2.2.0>)

Axway CLI includes the following enhancements:

* CLI extension packages are checked for updates and notification is displayed in the banner message.
* 32-bit architecture support deprecation warning is displayed in the banner.
* Support for authenticating a service account and upgrade to platform account using tooling credentials.
* Auth login --client-secret flow is a non-interative command only.
* The org view displays org teams and child orgs have been removed.
* Org and User activity changes are correctly displayed.
* Org usage is correctly including bundles and unlimited quotas.
* Directory/file permissions are automatically set when running as sudo.
* Show list of packages to update/purge and prompt to continue.
* Removed dependency on Registry Server with direct npm queries.
* Package name and version displayed during installation.
* Fixed --json output when result is undefined.
* Fixed error of overwriting the Axway CLI config when installing packages.

The Axway Central CLI is a package for managing Amplify Central resources with a DevOps approach to API Management.

**Axway Central CLI** version 1.21.0 is now available on NPM (<https://www.npmjs.com/package/@axway/axway-central-cli/v/1.21.0>).

The Axway Central CLI extension is compatible with the Axway CLI **version 2.2.0** (<https://www.npmjs.com/package/axway/v/2.1.0>).

The Axway Central CLI includes the following enhancements:

* An API Provider can manage or group similar or duplicate API Services together in an asset resource with a mapping template.
* The deletion of specific resource which has the same name in multiple scopes can be accomplished by specifying a scope parameter.

### Amplify Central WebUI

The Amplify Central WebUI is used by both the API providers and consumers to manage and consume APIs.

The Amplify Central WebUI includes the following enhancements:

* The Topology Environments list page performance as been improved.
* Service Mesh v1 support has been removed.

## Fixed issues

The following issues are fixed in this version of Amplify Central:

* **Amplify Central CLI is not able to create a service account when path contains space**. Previously, On windows machine, when using the `axway central create service-account` command, the command failed if the path contained a space. Now, long path or path containing space are handled correctly and service account can be created from any path.
* **Long endpoint names that contained a period cannot be created**. Previously, when creating an endpoint with a name containing a period, the endpoint cold not be created. Now, the endpoint having period in its name can be created.

## Known limitations

This version of Amplify Central has the following limitations:

* API Observer:

    * Users that are assigned the Consumer role cannot see their subscription usage on the API Observer screen.
