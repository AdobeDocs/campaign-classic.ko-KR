---
product: campaign
title: Campaign의 받은 편지함 렌더링
description: 전자 메일 주소를 캡처하여 전용 보고서에서 사용할 수 있도록 하는 방법을 알아봅니다
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---

# 받은 편지함 렌더링{#inbox-rendering}

## 받은 편지함 렌더링 기본 정보 {#about-inbox-rendering}

**보내기** 단추를 누르기 전에 메시지가 다양한 웹 클라이언트, 웹 메일 및 장치에서 수신자에게 최적의 방식으로 표시되는지 확인하십시오.

이를 위해 Adobe Campaign은 [Litmus](https://litmus.com/email-testing) 웹 기반 이메일 테스트 솔루션을 활용하여 렌더링을 캡처하고 전용 보고서에서 사용할 수 있도록 합니다. 이렇게 하면 수신될 수 있는 다른 컨텍스트에서 전송된 메시지를 미리 보고 주요 데스크톱 및 응용 프로그램의 호환성을 확인할 수 있습니다.

Litmus는 다양한 기능을 갖춘 이메일 유효성 검사와 미리 보기 응용 프로그램입니다. 이메일 콘텐츠 생성자는 Gmail 받은 편지함 또는 Apple Mail 클라이언트와 같은 70개 이상의 이메일 렌더러에서 메시지 콘텐츠를 미리 볼 수 있습니다.

Adobe Campaign의 **받은 편지함 렌더링에 사용할 수 있는 모바일, 메시징 및 웹 메일 클라이언트는 [Litmus 웹 사이트](https://litmus.com/email-testing)(**&#x200B;모든 이메일 클라이언트 보기&#x200B;**클릭)에 나열되어 있습니다.**

>[!NOTE]
>
>수신함 렌더링은 게재의 개인화를 테스트하는 데 필요하지 않습니다. **[!UICONTROL Preview]** 및 [증명](steps-validating-the-delivery.md#sending-a-proof)과 같은 Adobe Campaign 도구를 사용하여 개인화를 확인할 수 있습니다.

## 받은 편지함 렌더링 활성화 {#activating-inbox-rendering}

호스팅 및 하이브리드 클라이언트의 경우, 받은 편지함 렌더링은 Adobe 기술 지원 및 컨설턴트에 의해 인스턴스에 구성됩니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

온-프레미스 설치의 경우 아래 단계에 따라 받은 편지함 렌더링을 구성합니다.

1. **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 메뉴를 통해 **[!UICONTROL Inbox rendering (IR)]** 패키지를 설치합니다. 자세한 내용은 [Campaign Classic 표준 패키지 설치](../../installation/using/installing-campaign-standard-packages.md)를 참조하십시오.
1. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 노드를 통해 HTTP 유형의 외부 계정을 구성합니다. 자세한 내용은 [외부 계정 만들기](../../installation/using/external-accounts.md#creating-an-external-account)를 참조하십시오.
1. 외부 계정 매개 변수를 다음과 같이 설정합니다.
   * **[!UICONTROL Label]**:게재 기능 서버 정보
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**:없음
   * **[!UICONTROL Enabled]** 옵션을 선택합니다.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 노드로 이동합니다. **[!UICONTROL DmRendering_cuid]** 옵션을 검색하고 지원 팀에 연락하여 **[!UICONTROL Value (text)]** 필드에 복사해야 하는 게재 보고서 식별자를 가져옵니다.
1. **serverConf.xml** 파일을 편집하여 Litmus 서버에 대한 호출을 허용합니다. `<urlPermission>` 섹션에 다음 줄을 추가합니다.

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

## 리트머스 토큰 정보 {#about-litmus-tokens}

Litmus는 타사 서비스이므로 크레딧별 사용 모델로 작동합니다. 사용자가 리트머스 기능을 호출할 때마다 크레딧이 제외됩니다.

Adobe Campaign에서 크레딧은 사용 가능한 렌더링(토큰으로 알려져 있음)의 수에 해당합니다.

>[!NOTE]
>
>사용할 수 있는 리트머스 토큰 수는 구입한 Campaign 라이선스에 따라 다릅니다. 사용권 계약을 확인하십시오.

게재에서 **[!UICONTROL Inbox rendering]** 기능을 사용할 때마다 생성된 각 렌더링은 사용 가능한 토큰을 하나씩 감소시킵니다.

>[!IMPORTANT]
>
>토큰은 각 개별 렌더링에 대해 계산되며 전체 받은 편지함 렌더링 보고서가 아닙니다. 즉, 다음과 같습니다.
>
>* 받은 편지함 렌더링 보고서가 생성될 때마다 메시징 클라이언트당 하나의 토큰이 공제됩니다.Outlook 2000 렌더링을 위한 토큰 1개, Outlook 2010 렌더링을 위한 토큰, Apple Mail 9 렌더링을 위한 토큰 등.
>* 동일한 게재의 경우, 받은 편지함 렌더링을 다시 생성하는 경우 사용 가능한 토큰 수가 생성된 렌더링 수로 다시 감소합니다.

>



나머지 사용 가능한 토큰 수는 [받은 편지함 렌더링 보고서](#inbox-rendering-report)의 **[!UICONTROL General summary]**&#x200B;에 표시됩니다.

![](assets/s_tn_inbox_rendering_tokens.png)

일반적으로 받은 편지함 렌더링 기능은 새로 디자인된 이메일의 HTML 프레임워크를 테스트하는 데 사용됩니다. 각 렌더링에는 약 70개의 토큰이 필요합니다(일반적으로 테스트되는 환경 수에 따라 다름). 그러나 일부 경우에는 게재를 완전히 테스트하기 위해 여러 개의 받은 편지함 렌더링 보고서가 필요할 수 있습니다. 따라서 여러 점검을 완료하는 데 더 많은 토큰이 필요할 수 있습니다.

## 받은 편지함 렌더링 보고서 액세스 {#accessing-the-inbox-rendering-report}

전자 메일 게재를 만들고 타겟팅된 모집단과 해당 컨텐츠까지 정의했으면 아래 단계를 따르십시오.

게재 만들기, 디자인 및 타겟팅에 대한 자세한 내용은 [이 섹션](about-email-channel.md)을 참조하십시오.

1. 게재 상단 막대에서 **[!UICONTROL Inbox rendering]** 버튼을 클릭합니다.
1. **[!UICONTROL Analyze]** 을 선택하여 캡처 프로세스를 시작합니다.

   ![](assets/s_tn_inbox_rendering_button.png)

   증명을 보냅니다. 전자 메일을 보낸 후 몇 분 후에 렌더링 미리 보기에 액세스할 수 있습니다. 증명 보내기에 대한 자세한 내용은 [이 섹션](steps-validating-the-delivery.md#sending-a-proof)을 참조하십시오.

1. 전송 후 전송 목록에 증명이 나타납니다. 두 번 클릭합니다.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 증명의 **받은 편지함 렌더링** 탭으로 이동합니다.

   ![](assets/s_tn_inbox_rendering_tab.png)

   받은 편지함 렌더링 보고서가 표시됩니다.

## 받은 편지함 렌더링 보고서 {#inbox-rendering-report}

이 보고서는 수신자에게 표시되는 받은 편지함 렌더링을 표시합니다. 렌더링은 수신자가 전자 메일 게재를 여는 방법에 따라 다를 수 있습니다.브라우저, 모바일 장치 또는 이메일 애플리케이션을 통해서입니다.

**[!UICONTROL General summary]**&#x200B;은(는) 받은 메시지, 원치 않는 메시지(스팸), 받지 못한 메시지 또는 수신 대기 중인 메시지 수를 목록 및 그래픽 색상 코딩된 표현을 통해 보여 줍니다.

![](assets/s_tn_inbox_rendering_summary.png)

차트 위로 마우스를 가져가면 각 색상에 대한 세부 정보가 표시됩니다.

보고서 본문은 세 부분으로 나뉘어져 있습니다.**[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** 및 **[!UICONTROL Webmails]** 보고서를 아래로 스크롤하여 이 세 가지 범주로 그룹화된 모든 렌더링을 표시합니다.

![](assets/s_tn_inbox_rendering_report.png)

각 보고서에 대한 세부 정보를 보려면 해당 카드를 클릭합니다. 선택한 수신 방법에 대해 렌더링이 표시됩니다.

![](assets/s_tn_inbox_rendering_example.png)
