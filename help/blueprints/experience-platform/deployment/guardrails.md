---
title: Experience Platform and Application Guardrails 
description: Guardrails define the performance expectations and impact for the components and services within Adobe Experience Platform and Applications
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
---
# Guardrails

Guardrails are recommended thresholds that provide guidance for data, observed latencies and system usage in Adobe Experience Platform and applications. Guardrails reflect system constraints and performance expectations to optimize customer architecture and use case performance, and help to avoid errors or unexpected results. Guardrails are not intended to be service level agreements, service level agreements are documented in the Product Descriptions linked below and in the customer license agreements. Guardrails are intended to provide guidance in architecting solutions for specific customer use cases to ensure stability and execution.

For information on specific service level agreements for applications and features, refer to the [Application and feature descriptions](#application-feature-descriptions) section at the bottom of this page.

Note that for any customer use case that has strict latency or volume requirements, Adobe recommends reviewing your use case in detail with your Adobe Account Team and Implementation partner. In certain cases it is advisable to test and observe a given use case implementation prior to production launch of the use case to observe and understand expected behavior - as each customer implementation has varying factors at play including the nature and cadence of data ingestion, the specifics of the segment rules being built and the various activation channels and payloads - each use case implementation will have varying observed performance. As such it is best to establish and test the expected performance up front to ensure proper architecture and implementation according to the latency and performance requirements of the use case. 


## Guardrails Reference Documentation for Adobe Experience Platform and Applications

The following pages provide information about guardrails for Adobe Experience Platform features, services, and applications:

**Experience Platform applications**

* [Real-Time CDP guardrails overview](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics audience sharing guardrails](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Customer Journey Analytics data ingestion guardrails](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform services**

* [Data ingestion guardrails](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API Guardrails](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Real-time Customer Profile and Segmentation Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [Identity Guardrails](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=en)
* [Query Service Guardrails](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en)
* [Destination Activation Guardrails](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html)

## End-to-end latency diagrams {#end-to-end-latency}

### Experience Platform Edge Network and Hub Primary Observed Latencies {#edge-hub-latencies}

The following diagram depicts the primary edge and hub observed latencies to be aware of when architecting use case on the Experience Platform and Applications. 

![Experience Platform [!DNL Edge Network] and hub primary observed latencies.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency.svg "Experience Platform Edge Network and hub primary observed latencies"){width="1000" zoomable="yes"}

### Data ingestion {#data-ingestion}

The diagram below displays expected data ingestion latency values through [streaming ingestion](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) and [batch ingestion](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=en) when bringing data into Real-Time CDP. Click the image to see a high-resolution version.

![Data ingestion high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Data ingestion high-level visual overview and latency values"){width="1000" zoomable="yes"}

### Segmentation {#segmentation}

The diagram below displays expected latency values when working with audiences in the [Real-Time CDP segmentation service](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html). Click the image to see a high-resolution version.

![Segmentation high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Segmentation high-level visual overview and latency values"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform & [!DNL Edge Network] {#adobe-edge-latency}

The diagram below displays expected latency values when leveraging the [!DNL Edge Network] - for example to leverage RTCDP audiences in [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en). Click the image to see a high-resolution version.

![Adobe Edge Network and Experience Platform high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "Exporting audiences to Adobe Target high-level visual overview and latency"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

The diagram below displays expected latency values when working with [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Click the image to see a high-resolution version.

![Working with Customer Journey Analytics high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Working with Customer Journey Analytics high-level visual overview and latency values"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

The diagram below displays expected latency values when working with [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Click the image to see a high-resolution version.

![Working with Adobe Journey Optimizer high-level visual overview.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Working with Adobe Journey Optimizer high-level visual overview and latency values"){width="1000" zoomable="yes"}

## Application and feature descriptions {#application-feature-descriptions}

For information on feature-specific service level agreements, refer to the product descriptions below:

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [B2B Customer Data Platform](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform Activation](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Intelligent Services](https://helpx.adobe.com/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Journey Orchestration](https://helpx.adobe.com/legal/product-descriptions/journey-orchestration.html)
* [Offer Decisioning](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
