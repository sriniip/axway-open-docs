---
title: Amplify agents July 2021 Release Notes
linkTitle: Amplify agents July 2021
weight: 90
date: 2021-07-26
description: Traceability and Discovery agents for APIM Gateway / AWS / Azure provide better visibility into your multi-type gateway eco system. These agents collect data from the Gateway (API / traffic) and expose it in Amplify Central, providing you with a global vision of your eco system from a single interface.
---

## New features and enhancements

The following new features and enhancements are available in this update.

### Axway APIM Gateway agents

### AWS Gateway agents

### Azure agents

## Fixed issues

The following agent issues are fixed in this version of Amplify Central:

* **Add fix here**.

## Known limitations

This version of Amplify Central has the following limitations:

* Axway APIM Gateway agents:

    * Discovery Agent cannot expose discovered APIs in multiple teams, so the organization structure on API Manager is lost in Amplify Central. As a result, the API provider must create the team in Amplify Platform and share the API within the appropriate teams.
    * When an API is renamed in API Manager, Discovery Agent cannot recognize the API name change. This results in the API displaying in Amplify Central with dual entries of both the originally discovered name and the newly changed name.
    * When using the Gateway only capability without API Manager, Traceability Agent does not report the traffic.

* AWS Gateway agents:

    * Discovery Agent is working with only one AWS Region (the one used when installing the agent).
    * Discovery Agent can discover APIs having ANY method only, but consumers will not be able to subscribe to it from Unified Catalog.
    * Discovery Agent does not associate the usage plan and API when a subscriber chooses a usage plan that is not already linked to the chosen API.
    * The Usage report is not scalable, as the agent relies on AWS Simple Queue Service and cannot have more than 10 consumers per queue. It is possible to increase the number of workers on the agent side.

* Azure agents:

    * Discovery Agent does not manage revision and version.
    * Discovery Agent does not remove API Service and Catalog item when Azure API is removed.