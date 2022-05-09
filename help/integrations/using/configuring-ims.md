---
product: campaign
title: IMS 구성
description: Adobe ID을 통해 연결하는 방법 알아보기
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 4%

---

# IMS 구성{#configuring-ims}

![](../../assets/common.svg)

>[!IMPORTANT]
>
>Adobe IMS 구현은 Adobe 기술 관리자에게 엄격히 예약되어 있습니다. 구현 프로세스를 시작하려면 Adobe 담당자에게 문의하십시오.

## 전제 조건 {#prerequisites}

IMS와 통합을 사용하려면 다음을 수행하십시오.

* Adobe Experience Cloud 조직 이름과 ID가 있어야 합니다. 조직 ID를 찾으려면 다음을 참조하십시오 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko){_blank}.
* Experience Cloud에서 사용자를 추가해야 합니다. 자세한 내용은 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>사용자가 Adobe Campaign과 동기화될 Adobe Experience Cloud 그룹에 연결되어 있는지 확인합니다. [자세히 알아보기](#configuring-the-external-account)

## 콘솔 업데이트 {#updating-the-console}

이 기능을 사용하려면 반드시 최신 버전의 콘솔을 설치해야 합니다.

## 패키지 설치 {#installing-the-package}

기본 제공 설치 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지. 통합 패키지 설치는 에 자세히 설명되어 있는 표준 패키지를 설치하는 것과 같습니다 [이 페이지](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## 외부 계정 구성 {#configuring-the-external-account}

구성 **Adobe Experience Cloud** 외부 계정 **[!UICONTROL Administration > Platform > External accounts]**.

>[!CAUTION]
>
>이 구성은 기술 관리자용으로 예약되어 있습니다.

![](assets/ims_5.png)

다음 정보를 입력합니다.

* 사용된 IMS 서버에 대한 연결 정보(ID 및 암호)입니다. 이 정보는 Adobe 지원을 통해 제공됩니다. 자세한 내용은 [Adobe Experience Cloud 관리자를 위한 FAQ](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

   다음 **[!UICONTROL Callback server]** 주소는 **https**. 이 필드는 Adobe Campaign 인스턴스의 액세스 URL에 해당합니다.

* 조직 ID: 조직 ID를 찾으려면 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html){_blank}.
* 연결 마스크: 이 필드에서는 Adobe Campaign의 그룹과 Enterprise Dashboard의 구성 이름을 동기화할 수 있는 구문을 정의할 수 있습니다. Campaign - tenant_id - ( 구문을 사용하는 경우&#42;)&quot;로 설정되어 있는 경우, Adobe Campaign에서 만든 보안 그룹이 Enterprise Dashboard의 구성 이름 &quot;Campaign - tenant_id - internal_name&quot;에 연결됩니다.

   >[!CAUTION]
   >
   >Adobe ID을 통한 연결이 올바르게 작동하려면 연결 마스크가 필요합니다.

* Adobe Experience Cloud 연결 정보, 특히 Adobe Experience Cloud 테넌트의 이름입니다.
