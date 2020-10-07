---
title: IMS 구성
seo-title: IMS 구성
description: IMS 구성
seo-description: null
page-status-flag: never-activated
uuid: b659d29f-2a27-4a7b-b5ca-f44c3271dd4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: 279d0548-c876-4d5f-a195-48618bd5e9d1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 2%

---


# Configuring IMS{#configuring-ims}

## 사전 요구 사항 {#prerequisites}

IMS와의 통합을 사용하려면:

* Adobe Experience Cloud 조직 및 IMS ID가 있어야 합니다(Adobe Experience Cloud에 처음 연결할 때 제공).
* Experience Cloud에 사용자를 추가해야 합니다. 자세한 정보는 이 [페이지](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html)를 참조하십시오.

>[!NOTE]
>
>사용자가 Adobe Campaign과 동기화될 Adobe Experience Cloud 그룹에 연결되어 있는지 확인합니다. 외부 계정 [구성을 참조하십시오](#configuring-the-external-account).

## 콘솔 업데이트 {#updating-the-console}

이 기능을 사용하려면 최신 버전의 콘솔을 설치해야 합니다.

## 패키지 설치 {#installing-the-package}

패키지를 **[!UICONTROL Integration with the Adobe Experience Cloud]** 설치해야 합니다. 통합 패키지 설치는 표준 패키지를 설치하는 것과 같습니다. 이 [페이지에 자세히 설명되어 있습니다](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## 외부 계정 구성 {#configuring-the-external-account}

에서 **Adobe Experience Cloud** 외부 계정을 구성합니다 **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>이 구성은 기술 관리자를 위한 것입니다.

![](assets/ims_5.png)

다음 정보를 입력합니다.

* 사용된 IMS 서버의 연결 정보(ID 및 암호). 이 정보는 Adobe 지원으로 제공됩니다. 자세한 내용은 Adobe Experience Cloud 관리자를 위한 [FAQ를 참조하십시오](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/faq.html).

   주소는 **[!UICONTROL Callback server]** https ****&#x200B;로 지정해야 합니다. 이 필드는 Adobe Campaign 인스턴스의 액세스 URL에 해당합니다.

* IMS 조직 ID:이 정보는 Experience Cloud( in **[!UICONTROL Administration > Experience Cloud Details]** )에서 사용할 수 있으며 Adobe Experience Cloud에 처음 연결할 때 제공됩니다.
* 연결 마스크:이 필드를 사용하면 Enterprise Dashboard의 구성 이름을 Adobe Campaign의 그룹과 동기화할 수 있는 구문을 정의할 수 있습니다. &quot;Campaign - tenant_id - (.*)&quot;, Adobe Campaign에서 만든 보안 그룹이 Enterprise Dashboard의 구성 이름 &quot;Campaign - tenant_id - internal_name&quot;에 연결됩니다.

   >[!CAUTION]
   >
   >연결 마스크는 Adobe ID을 통한 연결이 올바르게 작동하기 위해 필요합니다.

* Adobe Experience Cloud 연결 정보, 특히 Adobe Experience Cloud 테넌트의 이름입니다.

