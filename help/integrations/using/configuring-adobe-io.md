---
product: campaign
title: Adobe Experience Cloud Triggers용 Developer Console 구성
description: Developer Console Adobe Experience Cloud Triggers 구성 방법 알아보기
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8d15a5666b5768bc0f17a4391061c4fcb9f76811
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# Adobe Experience Cloud Triggers용 Developer Console 구성 {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## 필수 구성 요소 {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

이 구현을 시작하기 전에 다음을 확인하십시오.

* 올바른 **조직 식별자**: 조직 ID는 Adobe Experience Cloud 내의 고유 식별자이며, 예를 들어 VisitorID 서비스 및 IMS SSO(Single Sign-On)에 사용됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko)
* 조직에 대한 **개발자 액세스**. 조직의 시스템 관리자는 트리거와 연결된 Adobe Analytics 제품의 `Analytics - {tenantID}` 제품 프로필에 대한 개발자 액세스 권한을 제공하려면 **단일 제품 프로필에 개발자 추가** 절차(이 페이지의 [설명](https://helpx.adobe.com/enterprise/using/manage-developers.html))를 따라야 합니다.

## 1단계: OAuth 프로젝트 만들기/업데이트 {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> 서비스 계정(JWT) 자격 증명은 Adobe에서 더 이상 사용되지 않으며, Adobe 솔루션 및 앱과 Campaign 통합은 이제 OAuth 서버 간 자격 증명을 사용해야 합니다. </br>
>
> * Campaign과 인바운드 통합을 구현한 경우 [이 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank)에 설명된 대로 기술 계정을 마이그레이션해야 합니다. 기존 [서비스 계정(JWT) 자격 증명](oauth-technical-account.md)은(는) 2025년 1월 27일까지 계속 작동합니다.</br>
>
> * Campaign-Analytics 통합 또는 Experience Cloud 트리거 통합과 같은 아웃바운드 통합을 구현한 경우 2025년 1월 27일까지 계속 작동합니다. 그러나 해당 날짜 이전에 Campaign 환경을 v7.4.1로 업그레이드하고 기술 계정을 oAuth로 마이그레이션해야 합니다.

Adobe Analytics 커넥터 구성을 계속하려면 Adobe Developer 콘솔에 액세스하고 OAuth 서버 간 프로젝트를 만듭니다.

자세한 설명서는 [이 페이지](oauth-technical-account.md#oauth-service)를 참조하세요.

## 2단계: Adobe Campaign에서 프로젝트 자격 증명 추가 {#add-credentials-campaign}

[이 페이지](oauth-technical-account.md#add-credentials)에 설명된 단계에 따라 Adobe Campaign에서 OAuth 프로젝트 자격 증명을 추가하십시오.

## 3단계: 파이프라인된 태그 업데이트 {#update-pipelined-tag}

[!DNL pipelined] 태그를 업데이트하려면 다음과 같이 구성 파일 **config-&lt; instance-name >.xml**&#x200B;에서 Developer Console 프로젝트에 인증 유형을 업데이트해야 합니다.

```
<pipelined ... authType="imsJwtToken"  ... />
```

그런 다음 `config -reload`을(를) 실행하고 [!DNL pipelined]을(를) 다시 시작하여 변경 내용을 고려하십시오.
