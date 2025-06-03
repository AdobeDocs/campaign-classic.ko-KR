---
product: campaign
title: 개인 정보 보호 요청 관리
description: 개인 정보 보호 요청에 대해 알아보기
feature: Privacy, Privacy Tools
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: c7688c2a-f0a7-4c51-a4cf-bf96fe8bf9b6
source-git-commit: 42cec0e9bede94a2995a5ad442822512bda14f2b
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 92%

---

# 개인 정보 보호 요청 정보 {#privacy-requests}



개인 정보 관리에 대한 일반 프레젠테이션은 [이 섹션](privacy-management.md)을 참조하십시오.

이 정보는 GDPR, CPA, PDPA 및 LGPD에 적용됩니다. 이러한 규정에 대한 자세한 내용은 [이 섹션](privacy-management.md#privacy-management-regulations)을 참조하십시오.

>[!NOTE]
>
>CPA에만 해당되는 개인 정보 판매 옵트아웃은 [이 섹션](#sale-of-personal-information-ccpa)에 설명되어 있습니다.

<!--Installation procedures described in this document are applicable starting Campaign Classic 18.4 (build 8931+). If you are running on a previous version, refer to this [technote](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html).-->

Adobe Campaign을 사용하면 개인 정보 보호 준비를 용이하게 하기 위해 액세스 및 삭제 요청을 처리할 수 있습니다. **액세스 권한** 및 **잊혀질 권리(삭제 요청)**&#x200B;는 [이 섹션](privacy-management.md#right-access-forgotten)에 설명되어 있습니다.

Adobe Campaign은 데이터 컨트롤러에게 개인 정보 보호 액세스 및 삭제 요청을 수행하는 두 가지 방법을 제공합니다.

* **Adobe Campaign 인터페이스를 통해** 각 개인 정보 보호 요청을 하는 경우 데이터 컨트롤러는 Adobe Campaign에서 새로운 개인 정보 보호 요청을 생성합니다. [이 섹션](privacy-requests-ui.md)을 참조하십시오.
*  **API**&#x200B;를 통해 Adobe Campaign은 SOAP를 사용한 개인 정보 보호 요청 자동 프로세스를 허용하는 API를 제공합니다. [이 섹션](privacy-requests-api.md)을 참조하십시오.

>[!NOTE]
>
>* 개인 데이터 및 데이터를 관리하는 다른 엔터티(데이터 컨트롤러, 데이터 프로세서 및 데이터 주체)에 대한 자세한 내용은 [개인 데이터 및 가상 사용자](privacy-and-recommendations.md#personal-data)를 참조하십시오.
>* 개인 정보 보호 요청에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/privacy/privacy){target=_blank}를 참조하세요.

<!--
## Prerequisites {#prerequesites}

Adobe Campaign offers Data Controllers tools to create and process Privacy requests for data stored in Adobe Campaign. However, it is the Data Controller's responsibility to handle the relationship with the Data Subject (email, customer care or a web portal).

It is therefore your responsibility as a Data Controller to confirm the identity of the Data Subject making the request and to confirm that the data returned to the requester is about the Data Subject.

## Installing the Privacy package {#install-privacy-package}

In order to use this feature, you need to install the **[!UICONTROL Privacy Data Protection Regulation]** package via the **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** > **[!UICONTROL Adobe Campaign Package]** menu. For more information on how to install packages, refer to the [detailed documentation](../../installation/using/installing-campaign-standard-packages.md).

Two new folders, specific to Privacy, are created under **[!UICONTROL Administration]** > **[!UICONTROL Platform]**:

* **[!UICONTROL Privacy Requests]**: this is where you will create your Privacy requests and track their evolution.
* **[!UICONTROL Namespaces]**: this is where you will define the field that will be used to identify the Data Subject in the Adobe Campaign database.

![](assets/privacy-folders.png)

In **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**, three technical workflows run every day to process Privacy requests.

![](assets/privacy-workflows.png)

* **[!UICONTROL Collect privacy requests]**: this workflow generates the recipient's data stored in Adobe Campaign and makes it available for download in the privacy request's screen.
* **[!UICONTROL Delete privacy requests data]**: this workflow deletes the recipient's data stored in Adobe Campaign.
* **[!UICONTROL Privacy request cleanup]**: this workflow erases the access request files that are older than 90 days.

In **[!UICONTROL Administration]** > **[!UICONTROL Access Management]** > **[!UICONTROL Named rights]**, the **[!UICONTROL Privacy Data Right]** named right has been added. This named right is required for Data Controllers in order for them to use privacy tools. This allows them to create new requests, track their evolution, use the API, etc.

![](assets/privacy-right.png)

## Namespaces {#namesspaces}

Before creating Privacy requests, you need to define the namespace you will use. This is the key that will be used to identify the Data Subject in the Adobe Campaign database.

Three namespaces are available out-of-the-box: email, phone and mobile phone. If you need a different namespace (a recipient custom field, for example), you can create a new one from **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Namespaces]**.

>[!NOTE]
>
>For optimal performance, it is recommended to use out-of-the-box namespaces.
-->