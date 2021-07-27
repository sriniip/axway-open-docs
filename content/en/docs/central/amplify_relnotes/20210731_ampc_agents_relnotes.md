---
title: Amplify agents July 2021 Release Notes
linkTitle: Amplify agents July 2021
weight: 90
date: 2021-07-26
description: Traceability and Discovery agents for Amplify Gateway / AWS / Azure / Istio provide better visibility into your multi-type gateway eco system. These agents collect data from the Gateway (API / traffic) and expose it in Amplify Central, providing you with a global vision of your eco system from a single interface.
---

## Versioning

Current available version is 1.0.12 based on Amplify Agents SDK v1.0.12.
Each agent can show this information using the `agentName --version` command.

## New features and enhancements

The following new features and enhancements are available in this update.

### Amplify Gateway agents enhancements

* Traceability agent report Gateway traffic even when Amplify Gateway is used without API Manager. Since there is no service name in this situation, all API usage will be visible in API Observer under the `APIGatewayOnly-noServiceName` API. The details of each transacation is visible in the API traffic section of API Observe as any other transaction.
* Traceability redaction feature is available for JMS properties. You can use the following properties: `TRACEABILITY_REDACTION_JMSPROPERTIES_SHOW` and `TRACEABILITY_REDACTION_JMSPROPERTIES_SANITIZE`. Refer to [JMS Trace redaction](/docs/central/connected_agent_common_reference/trace_redaction/#jms-properties-show-rules) and [JMS property sanitization](/docs/central/connected_agent_common_reference/trace_redaction/#jms-properties-value-sanitization-rules) topics.
* Last activity time is reported to the platform each time agents are sending data to the Platform and also for each agent health check trigger.

### Amplify AWS Gateway agents enhancements

* Use encrypted queues (default configuration) instead of standard queues.

### Amplify Azure agents enhancements

* None

### Amplify Istio agent enhancements

* Alignment with the latest Amplify Agents SDK brings the transaction redaction and the usage report capabilities.

## Fixed issues

The following agent issues are fixed in this version of Amplify Central:

* **Catalog items categories are lost when a consumer instance is updated**. Previously, when updating a consumer instance after a discovery process, the categories associated with the corresponding catalog item were lost. Now, before updating a consumer instance, the agent retrieve the most recent information from Amplify to keep existing categories.

## Known limitations

This version of Amplify agents has the following limitations:

* Amplify Gateway agents:

    * Discovery Agent cannot expose discovered APIs in multiple teams, so the organization structure on API Manager is lost in Amplify Central. As a result, the API provider must create the team in Amplify Platform and share the API within the appropriate teams.
    * When an API is renamed in API Manager, Discovery Agent cannot recognize the API name change. This results in the API displaying in Amplify Central with dual entries of both the originally discovered name and the newly changed name.
    * When using the Gateway only capability without API Manager, Traceability Agent does not report the traffic.

* Amplify AWS Gateway agents:

    * Discovery Agent is working with only one AWS Region (the one used when installing the agent).
    * Discovery Agent can discover APIs having ANY method only, but consumers will not be able to subscribe to it from Unified Catalog.
    * Discovery Agent does not associate the usage plan and API when a subscriber chooses a usage plan that is not already linked to the chosen API.
    * The Usage report is not scalable, as the agent relies on AWS Simple Queue Service and cannot have more than 10 consumers per queue. It is possible to increase the number of workers on the agent side.

* Amplify Azure agents:

    * Discovery Agent does not manage revision and version.
    * Discovery Agent does not remove API Service and Catalog item when Azure API is removed.

* Amplify Istio agents:

    * Discovery Agent cannot display its status in Central topology since is it not integrated with Amplify Agents SDK.
    * Discovery Agent requires manual set up to report API correctly.
    * Traceability Agent cannot leverage Amplify Agents SDK sampling feature.
