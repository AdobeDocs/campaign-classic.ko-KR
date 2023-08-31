---
product: campaign
title: Campaign의 받은 편지함 렌더링
description: 이메일 렌더링을 캡처하고 전용 보고서에서 사용할 수 있도록 하는 방법을 알아봅니다
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 9%

---

# 받은 편지함 렌더링{#inbox-rendering}

## 받은 편지함 렌더링 정보 {#about-inbox-rendering}

을(를) 누르기 전에 **보내기** 단추, 메시지가 다양한 웹 클라이언트, 웹 메일 및 디바이스에서 최적의 방식으로 수신자에게 표시되는지 확인합니다.

이를 위해 Adobe Campaign은 [리트머스](https://litmus.com/email-testing) 렌더링을 캡처하고 전용 보고서에서 사용할 수 있도록 하는 웹 기반 이메일 테스트 솔루션. 이렇게 하면 메시지가 수신될 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 보고 주요 데스크톱 및 응용 프로그램의 호환성을 확인할 수 있습니다.

>[!CAUTION]
>받은 편지함 렌더링이 와(과) 호환되지 않음 [반복 게재](communication-channels.md#recurring-delivery).
>

Litmus는 기능이 풍부한 이메일 유효성 검사 및 애플리케이션 미리보기입니다. 이를 통해 이메일 콘텐츠 작성자는 Gmail 받은 편지함 또는 Apple 메일 클라이언트와 같은 70개 이상의 이메일 렌더러에서 메시지 콘텐츠를 미리 볼 수 있습니다.

에 사용할 수 있는 모바일, 메시징 및 웹 메일 클라이언트 **받은 편지함 렌더링** Adobe Campaign의 목록은에 있습니다. [리트머스 웹사이트](https://litmus.com/email-testing) (클릭 **모든 이메일 클라이언트 보기**).

>[!NOTE]
>
>받은 편지함 렌더링은 게재에서 개인화를 테스트하는 데 필요하지 않습니다. 개인화는 다음과 같은 Adobe Campaign 도구를 사용하여 확인할 수 있습니다. **[!UICONTROL Preview]** 및 [증명](steps-validating-the-delivery.md#sending-a-proof).

## 받은 편지함 렌더링 활성화 {#activating-inbox-rendering}

[!BADGE 온-프레미스 및 하이브리드]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"}

호스팅 및 하이브리드 클라이언트의 경우 받은 편지함 렌더링은 Adobe 기술 지원 및 컨설턴트에 의해 인스턴스에서 구성됩니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

온-프레미스 설치의 경우 아래 단계에 따라 받은 편지함 렌더링을 구성합니다.

1. 설치 **[!UICONTROL Inbox rendering (IR)]** 를 통한 패키지 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴 아래의 제품에서 사용할 수 있습니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md).
1. 를 통해 HTTP 유형의 외부 계정 구성 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 노드. 자세한 내용은 [외부 계정 만들기](../../installation/using/external-accounts.md#creating-an-external-account).
1. 외부 계정 매개 변수를 다음과 같이 설정합니다.
   * **[!UICONTROL Label]**: 게재 기능 서버 정보
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: 없음
   * **[!UICONTROL Enabled]** 옵션을 선택합니다.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 로 이동 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 노드. 검색 **[!UICONTROL DmRendering_cuid]** 에 복사해야 하는 게재 보고서 식별자를 얻으려면 옵션 및 지원 센터에 문의 **[!UICONTROL Value (text)]** 필드.
1. 편집 **serverConf.xml** Litmus 서버에 대한 호출을 허용하는 파일입니다. 다음 줄을 추가합니다. `<urlPermission>` 섹션:

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

## Litmus 토큰 정보 {#about-litmus-tokens}

Litmus는 타사 서비스이므로 사용당 크레딧 모델을 기반으로 작동합니다. 사용자가 리트머스 기능을 호출할 때마다 크레딧이 공제됩니다.

Adobe Campaign에서 크레딧은 사용 가능한 렌더링(토큰으로 알려져 있음) 수에 해당합니다.

>[!NOTE]
>
>사용 가능한 Litmus 토큰의 수는 구입한 Campaign 라이선스에 따라 다릅니다. 사용권 계약을 확인하십시오.

을(를) 사용할 때마다 **[!UICONTROL Inbox rendering]** 게재 시 기능이며, 생성된 각 렌더링은 사용 가능한 토큰을 하나씩 감소시킵니다.

>[!IMPORTANT]
>
>토큰은 전체 받은 편지함 렌더링 보고서가 아닌 각 개별 렌더링을 고려합니다. 즉, 다음과 같습니다.
>
>* 받은 편지함 렌더링 보고서가 생성될 때마다 메시징 클라이언트당 하나의 토큰이 공제됩니다. Outlook 2000 렌더링용 토큰, Outlook 2010 렌더링용 토큰, Apple Mail 9 렌더링용 토큰 등이 있습니다.
>* 동일한 게재의 경우 받은 편지함 렌더링을 다시 생성하면 사용 가능한 토큰 수가 생성된 렌더링 수만큼 다시 감소합니다.
>

사용 가능한 나머지 토큰 수는 **[!UICONTROL General summary]** / [받은 편지함 렌더링 보고서](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

일반적으로 받은 편지함 렌더링 기능은 새로 디자인된 이메일의 HTML 프레임워크를 테스트하는 데 사용됩니다. 각 렌더링에는 일반적으로 테스트되는 환경의 수에 따라 약 최대 70개의 토큰이 필요합니다. 그러나 경우에 따라 게재를 완전히 테스트하기 위해 여러 받은 편지함 렌더링 보고서가 필요할 수 있습니다. 따라서 여러 검사를 완료하는 데 더 많은 토큰이 필요할 수 있습니다.

## 받은 편지함 렌더링 보고서 액세스 {#accessing-the-inbox-rendering-report}

전자 메일 게재를 만들고 타겟팅된 모집단과 해당 컨텐츠까지 정의했으면 아래 단계를 따르십시오.

게재 만들기, 디자인 및 타겟팅에 대한 자세한 내용은 을 참조하십시오. [이 섹션](about-email-channel.md).

1. 게재 상단 막대에서 **[!UICONTROL Inbox rendering]** 단추를 클릭합니다.
1. 선택 **[!UICONTROL Analyze]** 캡처 프로세스를 시작합니다.

   ![](assets/s_tn_inbox_rendering_button.png)

   증명이 전송되었습니다. 이메일을 보낸 후 몇 분 후에 해당 증명에서 렌더링 축소판에 액세스할 수 있습니다. 증명 전송에 대한 자세한 내용은 을 참조하십시오. [이 섹션](steps-validating-the-delivery.md#sending-a-proof).

1. 전송되면 게재 목록에 증명이 표시됩니다. 두 번 클릭합니다.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 로 이동 **받은 편지함 렌더링** 증명 탭입니다.

   ![](assets/s_tn_inbox_rendering_tab.png)

   받은 편지함 렌더링 보고서가 표시됩니다.

## 받은 편지함 렌더링 보고서 {#inbox-rendering-report}

이 보고서는 수신자에게 표시되는 받은 편지함 렌더링을 표시합니다. 렌더링은 브라우저, 모바일 디바이스 또는 이메일 애플리케이션 등 수신자가 이메일 게재를 여는 방법에 따라 다를 수 있습니다.

다음 **[!UICONTROL General summary]** 는 수신된 메시지, 원치 않는 메시지(스팸), 수신되지 않은 메시지 또는 수신 보류 중인 메시지 수를 목록으로, 그래픽 색상으로 구분된 표시를 통해 제공합니다.

![](assets/s_tn_inbox_rendering_summary.png)

차트 위로 마우스를 가져가면 각 색상에 대한 세부 정보가 표시됩니다.

보고서의 본문은 다음 세 부분으로 나뉘어져 있습니다. **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]**, 및 **[!UICONTROL Webmails]**. 보고서를 아래로 스크롤하여 이 세 가지 범주로 그룹화된 모든 렌더링을 표시합니다.

![](assets/s_tn_inbox_rendering_report.png)

각 보고서에 대한 세부 정보를 보려면 해당 카드를 클릭합니다. 선택한 수신 방법에 대해 렌더링이 표시됩니다.

![](assets/s_tn_inbox_rendering_example.png)
