---
product: campaign
title: IMS 구성
description: Adobe ID을 통해 연결하는 방법 알아보기
feature: Configuration
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 1%

---

# IMS 구성{#configuring-ims}

>[!IMPORTANT]
>
>Campaign 호스팅 또는 관리 서비스 사용자는 Adobe IMS 구현을 Adobe이 소유합니다. 아래에 설명된 단계는 온-프레미스 및 하이브리드 고객에게만 적용됩니다.
> Adobe IMS 구현은 Adobe 기술 관리자만 수행해야 합니다. 구현 프로세스를 시작하려면 Adobe 담당자에게 문의하십시오.

## 필수 구성 요소 {#prerequisites}

* Adobe Experience Cloud 조직 이름과 ID가 있어야 합니다. 조직 ID를 찾으려면 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko){_blank}를 참조하세요.
* Experience Cloud에 사용자를 추가해야 합니다. 자세한 정보는 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html?lang=ko){_blank}를 참조하세요.

>[!NOTE]
>
>사용자가 Adobe Campaign과 동기화할 Adobe Experience Cloud 그룹에 연결되어 있는지 확인합니다. [자세히 알아보기](#configuring-the-external-account).

## 콘솔 업데이트 {#updating-the-console}

이 기능을 사용하려면 최신 버전의 클라이언트 콘솔을 설치해야 합니다.

## 패키지 설치 {#installing-the-package}

기본 제공 **[!UICONTROL Integration with the Adobe Experience Cloud]** 패키지를 설치해야 합니다. 통합 패키지를 설치하는 것은 표준 패키지를 설치하는 것과 같습니다. 자세한 내용은 [이 페이지](../../installation/using/installing-campaign-standard-packages.md)를 참조하세요.

![](assets/ims_6.png)

## 외부 계정 구성 {#configuring-the-external-account}

**[!UICONTROL Administration > Platform > External accounts]**&#x200B;에서 **Adobe Experience Cloud** 외부 계정을 구성합니다.

![](assets/ims_5.png)

다음 정보를 입력합니다.

* 사용된 IMS 서버의 연결 정보(ID 및 암호). 이 정보는 Adobe 고객 지원 팀에서 제공합니다. 자세한 내용은 [Adobe Experience Cloud 관리자를 위한 FAQ](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html?lang=ko)를 참조하십시오.

  **[!UICONTROL Callback server]** 주소는 **https**&#x200B;에 지정해야 합니다. 이 필드는 Adobe Campaign 인스턴스의 액세스 URL에 해당합니다.

* 조직 ID: 조직 ID를 찾으려면 [이 페이지](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko){_blank}를 참조하세요.

* 연결 마스크: 이 필드에서는 Enterprise Dashboard의 구성 이름을 Adobe Campaign의 그룹과 동기화할 수 있는 구문을 정의할 수 있습니다. 구문 &quot;Campaign - tenant_id - (.&#42;)&quot;, Adobe Campaign에서 만든 보안 그룹은 Enterprise Dashboard의 구성 이름 &quot;Campaign - tenant_id - internal_name&quot;에 연결됩니다.

* Adobe Experience Cloud 연결 정보 - Adobe Experience Cloud 테넌트의 이름입니다.
