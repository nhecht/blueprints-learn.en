---
title: Multi-sandbox event-forwarding data collection
description: Learn how data collected with Experience Platform Web and Mobile SDKs can be configured to collect a single event and forwarded to multiple Experience Platform sandboxes.
solution: Data Collection
kt: 7202
exl-id: 3d9d312a-50b6-435f-b277-076e0c442a5f
---
# Multi-sandbox event-forwarding data collection

This blueprint shows how data collected with Experience Platform Web and Mobile SDKs can be configured to collect a single event and forward to multiple AEP sandboxes. This blueprint is specific to multi-sandbox data collection that uses [!UICONTROL Event Forwarding] to accomplish this goal.

In addition to replicating the event with [!UICONTROL Event Forwarding] features, you can add to, filter, or manipulate the original collected data that meet requirements for other sandboxes.

[!UICONTROL Event Forwarding] uses a separate property that contains the [!UICONTROL Data Elements], [!UICONTROL Rules], and [!UICONTROL Extensions] necessary for your data requirements. With an incoming event, your [!UICONTROL Event Forwarding] property can collect the data and manage as needed prior to forwarding.

Your destination sandbox requires a HTTP streaming end point configured that is used by the Adobe [!UICONTROL Cloud Connector] extension.

## Use cases

* Global data reporting - When using multiple sandboxes to isolate operating environments and the need to consolidate data collection to one sandbox for cross sandbox reporting. Routing an Experience Edge Event through [!UICONTROL Event Forwarding] to a reporting sandbox allows each sandbox operating environment to send data as it is collected in real time to a reporting sandbox.

* Manage data collection across sandboxes based on different data rules for each sandbox operating environment.

## Applications

* [!DNL Experience Platform] Data Collection
* [!UICONTROL Event Forwarding]
* AEP [!UICONTROL Extension]
* [!UICONTROL Cloud Connector Extension]

## Considerations

With [!UICONTROL Event Forwarding] as the approach to sending data to multiple sandboxes, there are considerations that must be taken into account with your solution architecture.

### No HIPAA Data

[!UICONTROL Event Forwarding] is not considered HIPAA Ready and should not be used in any HIPAA use cases where HIPAA data is collected. However, the infrastructure used for [!UICONTROL Event Forwarding] is deemed HIPAA ready and is solely at the discretion of the customer. While your [!UICONTROL Event Forwarding] Tag property resides in the [!UICONTROL Event Forwarding] system, the entire data payload collected is sent to the [!UICONTROL Event Forwarding] system for processing. It is this process that makes [!UICONTROL Event Forwarding] concerning for HIPAA use cases. With the entire payload shipped to the [!UICONTROL Event Forwarding] system, this would include any HIPAA values. Even though the [!UICONTROL Event Forwarding] rules will filter that data prior to sending to its destination, that HIPAA data is still shipped to a non HIPAA ready infrastructure. However, the payload data is never stored and is simply a pass through.

### Different datastreams and streaming end points

As data flows through datastreams from the [!UICONTROL Platform Edge Network], when using [!UICONTROL Event Forwarding] to another AEP sandbox, a requirement is to never use the same datastream or streaming end point as the datastream making the original collection. This can be detrimental to the AEP instance and potentially triggering a DoS situation.

### Estimated traffic volumes

Traffic volumes are required for review with each use case. This is important as high volumes could result in a throttling situation and customers are notified if this occurs.

## Architecture

![Multi-sandbox [!UICONTROL Event Forwarding]](assets/multi-sandbox-data-collection.png)

1. Collecting and sending event data to the [!UICONTROL Platform Edge Network] is required in order to use [!UICONTROL Event Forwarding]. Customers can use Adobe tags for client-side or the [!UICONTROL Platform Edge Network Server API] for server-to-server data collection. The [!UICONTROL Platform Edge Network API] can provide a server-to-server collection capability. This, however, does require a different programming model to implement. Refer to [Edge Network Server API Overview](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. Collected payloads are sent from tags implementation to the [!UICONTROL Platform Edge Network] to the [!UICONTROL Event Forwarding] service and processed by its own [!UICONTROL Data Elements], [!UICONTROL Rules] and [!UICONTROL Actions]. You can read more on the differences of [Tags and [!UICONTROL Event Forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. An [!UICONTROL Event Forwarding] property is also required to receive collected Event data from the [!UICONTROL Platform Edge Network]. Whether that event data was sent to the Platform Edge Network by a deployed Tags implementation or a server-to-server collection. Authors define the data elements, rules and actions used to enrich the event data prior to forwarding to the second sandbox. Consider using the custom code [!DNL JavaScript] data element to help with structuring your data for sandbox ingestion. Combined with Platform data prep capabilities, you have several options to manage your data structure.

1. Currently, the use of the Adobe [!UICONTROL Cloud Connector Extension] is required within the [!UICONTROL Event Forwarding] Property. Once the rules process or enrich the event data, the Cloud Connector is used within a fetch call configured for a POST sending the payload to the second sandbox

1. A streaming end point for data ingestion is required for the second sandbox. You can also consider Data Prep capabilities in AEP to help with ingestion and mapping of [!UICONTROL Event Forwarding] payloads to XDM. Refer to the AEP documentation Create a [HTTP API Streaming Connection using the UI](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=en)
