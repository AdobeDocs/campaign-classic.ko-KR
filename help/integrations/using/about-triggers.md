---
product: campaign
title: Adobe Experience Cloud Triggers 기본 정보
description: Adobe Experience Cloud 트리거 구현 시작
feature: Triggers
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Campaign 및 Experience Cloud 트리거 작업{#about-adobe-experience-triggers}

[!DNL Triggers]은(는) 파이프라인을 사용하여 Adobe Campaign과 Adobe Analytics 간의 통합입니다. 파이프라인은 사용자의 작업 또는 트리거를 웹 사이트에서 검색합니다. 장바구니 포기는 트리거의 예입니다. 트리거는 거의 실시간으로 이메일을 보내기 위해 Adobe Campaign에서 처리됩니다.

>[!CAUTION]
>
>이 기능은 제품의 일부로 기본 제공되지 않습니다. 이 구현을 위해 Adobe 담당자/고객 지원 팀과 협력합니다. 그러면 이 [페이지](../../integrations/using/configuring-pipeline.md#prerequisites)에 설명된 단계를 따를 수 있습니다.

[!DNL Triggers]은(는) 사용자의 작업 후 짧은 시간 내에 마케팅 작업을 실행합니다. 일반적인 응답 시간은 1시간 미만입니다.

구성이 최소한이고 서드파티가 관련이 없기 때문에 더 애자일 통합을 허용합니다.
또한 마케팅 활동의 성능에 영향을 주지 않고 많은 양의 트래픽을 지원합니다. 예를 들어 통합은 시간당 백만 개의 트리거를 처리할 수 있습니다.

![](assets/do-not-localize/book.png) [Experience Cloud 트리거를 만들고](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html)중요한 소비자 행동을 식별하고, 정의하고, 모니터링하는 방법을 알아봅니다.

## [!DNL Triggers] 아키텍처 {#triggers-architecture}

[!DNL pipelined] 프로세스가 항상 Adobe Campaign 마케팅 서버에서 실행되고 있습니다. 파이프라인에 연결하고 이벤트를 검색한 다음 즉시 처리합니다.

![](assets/triggers_2.png)

[!DNL pipelined] 프로세스가 인증 서비스를 사용하여 Experience Cloud에 로그인하고 개인 키를 보냅니다. 인증 서비스가 토큰을 반환합니다. 토큰을 사용하여 이벤트를 검색할 때 인증합니다.

## 필수 구성 요소 {#adobe-io-prerequisites}

이 구현을 시작하기 전에 다음을 확인하십시오.

* 올바른 **조직 식별자**: 조직 ID는 Adobe Experience Cloud 내의 고유 식별자이며, 예를 들어 VisitorID 서비스 및 IMS SSO(Single Sign-On)에 사용됩니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=ko)
* 조직에 대한 **개발자 액세스**. 조직의 시스템 관리자는 트리거와 연결된 Adobe Analytics 제품의 `Analytics - {tenantID}` 제품 프로필에 대한 개발자 액세스 권한을 제공하려면 **단일 제품 프로필에 개발자 추가** 절차(이 페이지의 [설명](https://helpx.adobe.com/enterprise/using/manage-developers.html))를 따라야 합니다.

## 구현 단계 {#implement}

Campaign 및 Experience Cloud 트리거를 구현하려면 아래 단계를 따르십시오.

1. OAuth 프로젝트를 만듭니다. [자세히 알아보기](oauth-technical-account.md#oauth-service)

1. Adobe Campaign에서 OAuth 프로젝트 자격 증명을 추가합니다. [자세히 알아보기](oauth-technical-account.md#add-credentials)

1. 다음과 같이 구성 파일 **config-&lt; instance-name >.xml**&#x200B;의 Developer Console 프로젝트에 인증 유형을 업데이트합니다.

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   그런 다음 `config -reload`을(를) 실행하고 [!DNL pipelined]을(를) 다시 시작하여 변경 내용을 고려하십시오.

