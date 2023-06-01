---
title: Multi Sandbox Event Forwarding Data Collection blueprint
description: Learn how data collected with Experience Platform Web and Mobile SDKs can be configured to collect a single event and forward to multiple AEP Sandboxes.
solution: Data Collection
kt: 7202
---

# Multi Sandbox Event Forwarding Data Collection blueprint

This blueprint shows how data collected with Experience Platform Web and Mobile SDKs can be configured to collect a single event and forward to multiple AEP Sandboxes. This blueprint is a specific use case for Multi Sandbox Data Collection that uses Event Forwarding to accomplish this goal.

In addition to replicating the event with Event Forwarding features, you can add to, filter, or manipulate the original collected data that meet requirements for other sandboxes.

Event Forwarding uses a separate property that contains the Data Elements, Rules, and Extensions necessary for your data requirements. With an incoming event, your Event Forwarding property can collect the data and manage as needed prior to forwarding.

Your destination sandbox requires a HTTP Streaming End Point configured that is used by the Adobe Cloud Connector extension.

## Use cases

* Global Data Reporting - When using multiple sandboxes to isolate operating environments and the need to consolidate Data Collection to one sandbox for cross sandbox reporting. Routing an Experience Edge Event through Event Forwarding to a reporting sandbox allows each sandbox operating environment to send data as it is collected in real time to a reporting sandbox
* Manage data collection across sandboxes based on different data rules for each sandbox operating environment.

## Applications

* Adobe Experience Platform Data Collection
* Event Forwarding
* AEP Extension
* Cloud Connector Extension

## Considerations

With Event Forwarding as the approach to sending data to multiple sandboxes, there are considerations that must be taken into account with your solution architecture.

### No HIPAA Data

Event Forwarding is not considered HIPAA Ready and should not be used in any HIPAA use cases where HIPAA data is collected. However, the infrastructure used for Event Forwarding is deemed HIPAA ready and is solely at the discretion of the customer. While your Event Forwarding Tag property resides in the Event Forwarding system, the entire data payload collected is sent to the Event Forwarding system for processing. It is this process that makes Event Forwarding concerning for HIPAA use cases. With the entire payload shipped to the Event Forwarding system, this would include any HIPAA values. Even though the Event Forwarding rules will filter that data prior to sending to its destination, that HIPAA data is still shipped to a non HIPAA ready infrastructure. However, the payload data is never stored and is simply a pass through.

### Different Datastreams and Streaming End Points

As data flows through Datastreams from the Platform Edge Network, when using Event Forwarding to another AEP Sandbox, a HARD requirement is to NEVER use the same Datastream or Streaming End Point as the Datastream making the original collection. This can be detrimental to the AEP instance and potentially triggering a DoS situation.

### Estimated traffic Volumes

Traffic volumes are required for review with each use case. This is important as high volumes could result in a throttling situation and customers will be notified if this occurs.

## Architecture

![Multi Sandbox Event Forwarding](assets/multi-sandbox-data-collection.png)

1. Collecting and sending Event data to the Platform Edge Network is required in order to use Event Forwarding. Customers can use Adobe Tags for client-side or the Platform Edge Network Server API for server-to-server data collection. The Platform Edge Network API can provide a server-to-server collection capability. This however does require a different programming model to implement. Refer to [Edge Network Server API Overview](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en)

1. Collected payloads are sent from Tags implementation to the Platform Edge Network to the Event Forwarding service and processed by its own Data Elements, Rules and Actions. You can read more on the differences of [Tags and Event Forwarding](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. An Event Forwarding Property is also required to receive collected Event data from the Platform Edge Network. Whether that Event data was sent to the Platform Edge Network by a deployed Tags implementation or a server-to-server collection. Authors define the data elements, rules and actions used to enrich the event data prior to forwarding to the second sandbox. Consider using the Custom Code JavaScript data element to help with structuring your data for sandbox ingestion. Combined with AEP Data Prep capabilities, you have several options to manage your data structure.

1. Currently, the use of the Adobe Cloud Connector Extension is required within the Event Forwarding Property. Once the Rules process or enrich the event data, the Cloud Connector is used within a Fetch Call configured for a POST sending the payload to the second sandbox

1. A Streaming End point for data ingestion is required for the second sandbox. You can also consider Data Prep capabilities in AEP to help with ingestion and mapping of Event Forwarding payloads to XDM. Refer to the AEP documentation Create a [HTTP API Streaming Connection using the UI](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=en)
