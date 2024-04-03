---
title: Multi Sandbox Event Forwarding Data Collection blueprint
description: Stream collected data by [!DNL Experience Platform] (AEP) SDKs to multiple sandboxes using Event Forwarding
solution: Data Collection
kt: 7202
exl-id: c24a47fe-b3da-4170-9416-74d2b6a18f32
---
# Multi-sandbox event-forwarding Data Collection blueprint

Multi-sandbox event-forwarding Data Collection blueprint shows how data collected with Adobe [!DNL Experience Platform] Web and Mobile SDKs can be configured to collect a single event and forward to multiple [!DNL Experience Platform] (AEP) sandboxes. This Blueprint is a specific use case that uses the Event Forwarding feature of Adobe Tags.

In addition to replicating the event, using the Event Forwarding features, you can add to, filter or manipulate the original collected data that meet requirements for other sandboxes. For instance Sandbox A needs to receive all event data elements and Sandbox B should only receive non PII data.

Event Forwarding uses a separate Tag property that contains the Data Elements, Rules and Extensions necessary for your data requirements. With an incoming Event, your Event Forwarding Property can collect the data and manage as needed prior to forwarding.

Your destination sandbox would need a HTTP Streaming End Point configured that would be used by the Event Forwarding HTTPS Extension.

## Use cases

* Global Data Reporting - When using multiple sandboxes to isolate operating environments and the need to consolidate Data Collection to one sandbox for cross sandbox reporting. Event Forward to a reporting sandbox allows each sandbox operating environment to send data as it is collected in real time to a reporting sandbox
* Manage data collection across sandboxes based on different data rules for each sandbox operating environment. Such operating environments that require filtering of sensitive data such as Healthcare and Financial Services

## Applications

* Adobe [!DNL Experience Platform] Data Collection

## Architecture

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Reference Architecture for Multi Sandbox Event Forwarding" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

1. Tag authors define both a tag property as well as a Event Forwarding Property. Here, authors define the data elements, rules and actions that manage data collection. Keep in mind, tag property code runs on the client and is distributed by a CDN Host. The [!UICONTROL Event Forwarding Property] code runs on the Adobe [!DNL Edge Server].

1. Data collected on the client is sent to the [!DNL Edge Network]. Customers also have the option to send data to their own server first as a method of server side collection. The Web SDK can provide a server-to-server collection capability. This however does require a different programming model to implement. Refer to the documentation **[!DNL Edge Network] Server API Overview** below

1. Platform [!DNL Edge Network] receives data collection payloads and orchestrates the flow of data to the required systems such as Target and Analytics.

1. Event forwarding property data elements are used to access event data arriving in the payload. Rules may also be used to manipulate the Event data as needed prior to forwarding. Such as formatting the data into the required XDM for streaming data ingestion

1. Event forwarding provides the HTTPS extension that provides the ability to forward your event data to a HTTPS end point.

1. Sandbox 2 is configured with a streaming end point that recieves the forwarded event.

## Related documentation

* [Event forwarding documentation](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)
* [Event forwarding videos](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html)
* [Event forwarding lesson](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html) of the Web SDK tutorial
* [[!DNL Experience Platform] Web SDK Overview](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [[!DNL Edge Network] Server API Overview](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

## Related blog posts

* [Boosting Website Performance with Adobe [!DNL Experience Platform] Web SDK and [!DNL Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [Solving Implementation Pain Points with Adobe [!DNL Experience Platform] Web SDK and [!DNL Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [Adobe [!DNL Experience Platform] Web SDK for Audience Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe [!DNL Experience Platform] Web SDK - Adobe Target](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [Adobe [!DNL Experience Platform] Web SDK Migration Scenarios for Adobe Analytics](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [Unify Your Adobe [!DNL Experience Platform] Services with Adobe [!DNL Experience Platform] Web SDK](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [Accelerate Your Mobile Application Development with Adobe [!DNL Experience Platform] Mobile SDK and Launch](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [Simplifying Customer Workflows with Adobe Experience Platform Web SDK](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
