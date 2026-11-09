---
product: campaign
title: Campaign의 받은 편지함 렌더링
description: 이메일 렌더링을 캡처하고 전용 보고서에서 사용할 수 있도록 하는 방법을 알아봅니다
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 8%
---
# 받은 편지함 렌더링{#inbox-rendering}

Adobe Campaign은 [Litmus](https://litmus.com/email-testing) 웹 기반 전자 메일 테스트 솔루션을 활용하여 전자 메일 렌더링을 캡처하고 전용 보고서에서 사용할 수 있도록 합니다.

>[!NOTE]
>
>Campaign v7에서 v8로 전환하는 과정의 일부로 Campaign Classic 설명서 세트가 간소화 및 재구성되었습니다. 이제 일반적인 기능은 Campaign v8 설명서 세트에서만 사용할 수 있습니다. 받은 편지함 렌더링에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}를 참조하세요.
>
>[![이미지](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## 받은 편지함 렌더링 활성화 {#activating-inbox-rendering}

[!BADGE 온-프레미스 및 하이브리드]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"}

호스팅 및 하이브리드 클라이언트의 경우 Adobe 기술 지원 및 컨설턴트에 의해 인스턴스에서 받은 편지함 렌더링을 구성합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

온-프레미스 설치의 경우 아래 단계에 따라 받은 편지함 렌더링을 구성합니다.

1. **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴를 통해 **[!UICONTROL Inbox rendering (IR)]** 패키지를 설치하십시오. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.
1. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 노드를 통해 HTTP 유형의 외부 계정을 구성합니다. 자세한 내용은 [외부 계정 만들기](../../installation/using/external-accounts.md#creating-an-external-account)를 참조하세요.
1. 외부 계정 매개 변수를 다음과 같이 설정합니다.
   * **[!UICONTROL Label]**: 게재 가능성 서버 정보
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: 없음
   * **[!UICONTROL Enabled]** 옵션을 선택합니다.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 노드로 이동합니다. **[!UICONTROL DmRendering_cuid]** 옵션을 검색하고 **[!UICONTROL Value (text)]** 필드에 복사해야 하는 게재 보고서 식별자를 가져오려면 지원 팀에 문의하십시오.
1. Litmus 서버를 호출할 수 있도록 **serverConf.xml** 파일을 편집합니다. `<urlPermission>` 섹션에 다음 줄을 추가합니다.

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 다음 명령을 사용하여 구성을 다시 로드합니다.

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>받은 편지함 렌더링을 사용하려면 콘솔에서 로그아웃한 다음 다시 로그인해야 할 수 있습니다.
