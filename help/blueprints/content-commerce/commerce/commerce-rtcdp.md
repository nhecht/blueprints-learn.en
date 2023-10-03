---
title: Adobe Commerce - RTCDP Blueprint
description: Adobe Experience Platform Integration with Adobe Commerce to create a single view of customers and intelligently personalize experiences on a digital storefront and across channels.
solution: Real-Time Customer Data Platform, Commerce

---
# Adobe Commerce & RTCDP

This integrated experience helps Adobe Commerce customers to seamlessly intergrate with Adobe Experience Platform to enrich the customer profile and personalize experience in digital storefront and other channels. 

## Technical Capablities Enabled

* Storefront data(client side) collected and sent into any Adobe Experience Cloud product. (add to cart, cart abandons,etc)
* Back office order status to any AEC product
* Back office historical orders can be sent to Adobe Experience Platform
* Share and personalize RTCDP audiences to Adobe Commerce

## Pre-requisites

To use the Experience Platform connector, you must have the following:

* Adobe Commerce 2.4.3 or newer
* Adobe ID and Organization ID
* Adobe Experience Platform/RT-CDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=en). The ACDL is required to collect storefront event data.

## Onboarding steps

### Data Collection from Adobe Commerce to Adobe Experience Platform

* [Install](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) the Experience Platform connector extension.
* [Sign in](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) to your Adobe account and view to confirm your organization ID. The organization ID is the ID associated with your provisioned Experience Cloud company. This ID is a 24-character alphanumeric string, followed by (and must include) @AdobeOrg.
* [Create or update](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/update-xdm.html?lang=en) your XDM schema with Commerce-specific field groups.
* [Create a dataset](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=en#create-a-dataset) based off the schema you created or updated. This dataset will contain the Commerce data you send.
* [Create a datastream](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) and select the XDM schema that contains the Commerce-specific field groups.
* [Connect to Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en).
* [Connect to Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/connect-data.html?lang=en).

### Connect to the Commerce Destination from AEP for Segment Sharing

To connect to the Adobe Commerce destination:

* In the [Platform interface](https://experience.adobe.com/platform/), go to Destinations > Catalog.
* Select Personalization.
* Select the Adobe Commerce destination to highlight it, then select Set up.
* Follow the steps described in the [destination configuration tutorial](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=en).

## Out-of-Box Data

* Storefront(Browser/App) Events
* Back office events
* Historical order data

For complete list of events supported, please refer to [Commerce Events](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/event-forwarding/events.html?lang=en)

## Architecture

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP architecture" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


## Related Implementation Guides

| Guide |Link|
|:----|:----|
|Platform Connector|[Adobe Commerce Experience Platform connector overview](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/overview.html?lang=en)|
|Commerce Destination|[Adobe Commerce Connection in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=en)|
|Edge Personalization|[Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=en)| |
