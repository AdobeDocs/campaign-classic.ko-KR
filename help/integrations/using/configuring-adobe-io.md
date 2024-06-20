---
product: campaign
title: Adobe Experience Cloud Triggers용 Developer Console 구성
description: Developer Console Adobe Experience Cloud Triggers을 구성하는 방법 알아보기
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
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

* 유효한 **조직 식별자**: 조직 ID는 Adobe Experience Cloud 내의 고유 식별자로서, 예를 들어 방문자 ID 서비스 및 IMS SSO(Single Sign-On)에 사용됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko)
* a **개발자 액세스** (으)로 가져왔습니다. 조직의 시스템 관리자는 **단일 제품 프로필에 개발자 추가** 프로시저 세부 정보 [이 페이지에서](https://helpx.adobe.com/enterprise/using/manage-developers.html) 개발자에게 다음에 대한 액세스 권한을 제공하려면 `Analytics - {tenantID}` 트리거와 연결된 Adobe Analytics 제품의 제품 프로필 .

## 1단계: OAuth 프로젝트 만들기/업데이트 {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> 서비스 계정(JWT) 자격 증명은 Adobe에서 더 이상 사용되지 않으며, Adobe 솔루션 및 앱과 Campaign 통합은 이제 OAuth 서버 간 자격 증명을 사용해야 합니다. </br>
>
> * Campaign과 인바운드 통합을 구현하면에 자세히 설명된 대로 기술 계정을 마이그레이션해야 합니다. [이 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). 기존 서비스 계정(JWT) 자격 증명은 2025년 1월 27일까지 계속 작동합니다.</br>
>
> * Campaign-Analytics 통합 또는 Experience Cloud 트리거 통합과 같은 아웃바운드 통합을 구현한 경우 2025년 1월 27일까지 계속 작동합니다. 그러나 해당 날짜 이전에 Campaign 환경을 v7.4.1로 업그레이드하고 기술 계정을 oAuth로 마이그레이션해야 합니다.

Adobe Analytics 커넥터 구성을 계속하려면 Adobe Developer 콘솔에 액세스하고 OAuth 서버 간 프로젝트를 만듭니다.

을(를) 참조하십시오 [이 페이지](oauth-technical-account.md#oauth-service) 을 참조하십시오.

## 2단계: Adobe Campaign에서 프로젝트 자격 증명 추가 {#add-credentials-campaign}

다음에 자세히 설명된 단계 수행 [이 페이지](oauth-technical-account.md#add-credentials) Adobe Campaign에서 OAuth 프로젝트 자격 증명을 추가할 수 있습니다.

## 3단계: 파이프라인된 태그 업데이트 {#update-pipelined-tag}

업데이트하려면 [!DNL pipelined] 태그: 구성 파일의 Developer Console 프로젝트에 인증 유형을 업데이트해야 합니다 **config-&lt; instance-name >.xml** 다음과 같이:

```
<pipelined ... authType="imsJwtToken"  ... />
```

그런 다음 를 실행합니다. `config -reload` 및 의 다시 시작 [!DNL pipelined] 를 참조하십시오.
