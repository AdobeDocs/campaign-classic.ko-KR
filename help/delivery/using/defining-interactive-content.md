---
solution: Campaign Classic
product: campaign
title: Adobe Campaign Classic에서 인터랙티브한 컨텐츠 정의
description: Adobe Campaign Classic에서 AMP를 사용하여 인터랙티브하고 다이내믹한 이메일 컨텐츠를 정의하는 방법을 살펴볼 수 있습니다.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 3%

---


# 대화형 콘텐츠 정의{#defining-interactive-content}

Adobe Campaign에서는 특정 조건에서 동적 이메일을 보낼 수 있는 새로운 대화형 [AMP for Email](https://amp.dev/about/email/) 형식을 사용할 수 있습니다.

AMP for Email을 사용하면 다음 작업을 수행할 수 있습니다.
* 적절하게 구성된 특정 주소로 AMP 이메일 배달을 테스트합니다.
* 해당 공급자에 등록한 후 Gmail, Outlook 또는 Mail.ru 주소로 AMP 이메일을 배달합니다.

AMP 이메일 테스트 및 전송에 대한 자세한 내용은 [AMP 이메일 타깃팅](#targeting-amp-email)을 참조하십시오.

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 이 패키지를 사용하려면 이 패키지를 설치해야 합니다. 작업이 완료되면 패키지를 고려하여 서버를 다시 시작합니다.

>[!NOTE]
>
> 하이브리드 및 호스팅 아키텍처의 경우 [중간 소싱 서버](../../installation/using/mid-sourcing-server.md) 및 [실행 인스턴스](../../message-center/using/creating-a-shared-connection.md#execution-instance)를 포함하여 모든 서버에 패키지를 설치해야 합니다. 계정 담당자에게 문의하십시오.

## 이메일 {#about-amp-for-email}에 대한 AMP 정보

이메일&#x200B;**용** AMP 새 형식을 사용하면 메시지 내에 AMP 구성 요소를 포함할 수 있으므로 풍부하고 실행 가능한 컨텐츠가 포함된 이메일 경험을 향상시킬 수 있습니다. 이메일 내에서 바로 이용할 수 있는 최신 앱 기능을 통해 수신자는 메시지 자체의 콘텐츠와 동적으로 상호 작용할 수 있습니다.

예제:
* AMP로 작성된 이메일에는 이미지 Carousel과 같은 대화형 요소가 포함될 수 있습니다.
* 컨텐츠는 메시지에서 최신 상태로 유지됩니다.
* 수신자는 받은 편지함을 떠나지 않고도 양식에 응답하는 것과 같은 작업을 수행할 수 있습니다.

이메일용 AMP가 기존 이메일과 호환됩니다. 메시지의 AMP 버전은 HTML 및/또는 일반 텍스트 외에 새로운 MIME 부분으로 이메일에 포함되므로 모든 이메일 클라이언트에서 호환되도록 합니다.

이메일 형식, 사양 및 요구 사항에 대한 AMP에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)를 참조하십시오.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#amp-email-video)

## Adobe Campaign {#key-steps-to-use-amp}에서 이메일에 AMP를 사용하는 주요 단계

Adobe Campaign에서 AMP 이메일을 성공적으로 테스트하고 보내려면 아래 단계를 따르십시오.
1. **[!UICONTROL AMP support]** 패키지를 설치합니다. [Campaign 표준 패키지](../../installation/using/installing-campaign-standard-packages.md) 설치를 참조하십시오.
1. Adobe Campaign에서 이메일을 만들어 AMP 콘텐츠를 제작할 수 있습니다. [Adobe Campaign](#build-amp-email-content)로 AMP 이메일 콘텐츠 작성을 참조하십시오.
1. AMP 형식을 지원하는 이메일 공급자의 모든 배포 요구 사항을 따라야 합니다. 이메일 배달 요구 사항](#amp-for-email-delivery-requirements)에 대한 [AMP를 참조하십시오.
1. 대상을 정의할 때 AMP 형식을 표시할 수 있는 받는 사람을 선택해야 합니다. [AMP 이메일 타깃팅](#targeting-amp-email)을 참조하십시오.

   >[!NOTE]
   >
   >현재 지원되는 이메일 클라이언트에서 [특정 이메일 주소](#testing-amp-delivery-for-selected-addresses)(테스트 목적) 또는 [등록 후](#delivering-amp-emails-by-registering)에만 AMP 이메일을 전달할 수 있습니다.

1. 평상시처럼 이메일 전송 [AMP 이메일 보내기](#sending-amp-email)를 참조하십시오.

## Adobe Campaign {#build-amp-email-content}에서 AMP 전자 메일 콘텐츠 빌드

AMP 형식을 사용하여 이메일을 작성하려면 아래 단계를 따르십시오.

>[!IMPORTANT]
>
>AMP for Email 요구 사항 및 사양에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)를 참조하십시오. 이메일 모범 사례](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)에 대해서는 [AMP를 참조할 수도 있습니다.

1. 이메일 배달을 만들 때 템플릿을 선택합니다.

   >[!NOTE]
   >
   >특정 AMP 템플릿에는 사용할 수 있는 기본 용량 예제가 포함되어 있습니다.제품 목록, carousel, 이중 옵트인, 설문 조사 및 고급 서버 요청

1. **[!UICONTROL AMP content]** 탭을 클릭합니다.

   ![](assets/amp_tab.png)

1. 필요에 맞게 AMP 콘텐츠를 편집합니다.

   >[!NOTE]
   >
   >첫 번째 AMP 이메일 작성에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)를 참조하십시오.

   예를 들어 AMP 템플릿의 제품 목록 구성 요소를 사용하고 타사 시스템 또는 Adobe Campaign 내에서 제품 목록을 유지 관리할 수 있습니다. 가격이나 다른 요소를 조정할 때마다 받는 사람이 사서함에서 이메일을 다시 열면 자동으로 반영됩니다.

1. 개인화 필드 및 개인화 블록을 통해 Adobe Campaign의 HTML 포맷과 같이 필요에 따라 AMP 컨텐츠를 개인화할 수 있습니다.

   ![](assets/amp_tab_perso.png)

1. 편집을 완료한 후 전체 AMP 내용을 선택하고 [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org) 또는 유사한 웹 사이트에 복사하여 붙여 넣습니다.

   >[!NOTE]
   >
   >화면 상단의 드롭다운 목록에서 **AMP4 EMAIL**&#x200B;을 선택해야 합니다.

   ![](assets/amp_validator.png)

   오류가 발생하면 인라인으로 플래그가 지정됩니다.

   >[!NOTE]
   >
   >Adobe Campaign AMP 편집기는 콘텐츠 유효성 검사를 위해 디자인되지 않았습니다. [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org)와 같은 외부 웹 사이트를 사용하여 내용이 올바른지 확인하십시오.

1. AMP 내용이 유효성 검사를 통과할 때까지 필요에 따라 수정합니다.

   ![](assets/amp_validator_pass.png)

1. 유효성이 검증된 컨텐츠를 [AMP 놀이터](https://playground.amp.dev) 또는 유사한 웹 사이트에 복사하여 붙여넣으면 컨텐츠를 미리 볼 수 있습니다.

   >[!NOTE]
   >
   >화면 상단의 드롭다운 목록에서 **이메일**&#x200B;에 대한 AMP를 선택해야 합니다.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Adobe Campaign에서 직접 AMP 콘텐츠를 미리 볼 수는 없습니다. [AMP 놀이터](https://playground.amp.dev)와 같은 외부 웹 사이트를 사용합니다.

1. Adobe Campaign으로 돌아가 유효성이 확인된 내용을 **[!UICONTROL AMP content]** 탭에 복사하여 붙여넣습니다.

1. **[!UICONTROL HTML content]** 또는 **[!UICONTROL Text content]** 탭으로 전환하고 이 두 형식 중 적어도 하나에 대한 내용을 정의합니다.

   >[!IMPORTANT]
   >
   >이메일에 AMP 내용 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않으면 보낼 수 없습니다.

## 전자 메일 배달 요구 사항 {#amp-for-email-delivery-requirements}

Adobe Campaign에서 AMP 컨텐츠를 작성할 때 수신자의 이메일 공급자에 따라 제공되는 동적 이메일의 조건을 준수해야 합니다.

현재 3개의 이메일 공급자가 이 형식을 테스트하는 것을 지원합니다.Gmail, Outlook 및 Mail.ru.

Gmail 계정에서 AMP 형식으로 배달을 테스트하는 데 필요한 모든 단계 및 사양은 해당 [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) 및 [Mail.ru](https://postmaster.mail.ru/amp) 개발자 문서에 자세히 설명되어 있습니다.

특히 다음 요구 사항을 충족해야 합니다.
* [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) 및 [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto)에 대한 AMP 보안 요구 사항을 따르십시오.
* AMP MIME 부분에 [유효한 AMP 문서](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)가 있어야 합니다.
* AMP MIME 부분은 100KB보다 작아야 합니다.

Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices)에 대한 [팁과 알려진 제한 사항 및 [AMP 우수 사례를 참조할 수도 있습니다.](https://developers.google.com/gmail/ampemail/tips)

## AMP 이메일 {#targeting-amp-email} 타게팅

현재 두 단계로 AMP 이메일 전송을 실험해 볼 수 있습니다.

1. Adobe Campaign을 사용하면 내용과 동작을 확인하기 위해 AMP 기반 동적 이메일을 선택한 이메일 주소로 적절하게 구성된 이메일 주소로 전달하는 것을 테스트할 수 있습니다. 선택한 주소](#testing-amp-delivery-for-selected-addresses)에 대해 [AMP 이메일 배달 테스트를 참조하십시오.

1. 테스트를 거친 후에는 관련 이메일 공급자에게 등록하여 보낸 사람 도메인을 허용 목록에 추가하도록 함으로써 이메일용 AMP 프로그램의 일부로 게재 또는 캠페인을 보낼 수 있습니다. 이메일 공급자](#delivering-amp-emails-by-registering)에 등록하여 [AMP 이메일 제공을 참조하십시오.

### 선택한 주소 {#testing-amp-delivery-for-selected-addresses}에 대한 AMP 이메일 배달 테스트

Adobe Campaign에서 선택한 이메일 주소로 동적 메시지 전송을 테스트할 수 있습니다.

>[!NOTE]
>
>현재 Gmail, Outlook 및 Mail.ru만 AMP 형식 테스트를 지원합니다.

Gmail 및 Outlook의 경우, 먼저 대상 Gmail 및 Outlook 계정에 대해 Adobe Campaign허용 목록에 추가하다에서 제공하기 위해에 사용하고 있는 보낸 사람 주소를 추가해야 합니다.

방법은 다음과 같습니다.
1. 관련 이메일 공급자에 대해 동적 이메일 활성화 옵션이 선택되어 있는지 확인합니다.
1. 배달의 **[!UICONTROL From]** 필드에 표시된 보낸 사람 주소를 복사하여 이메일 공급자 계정 설정의 해당 섹션에 붙여 넣습니다.

자세한 내용은 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 및 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) 개발자 설명서를 참조하십시오.

![](assets/amp_from_field.png)

Mail.ru 주소로 AMP 이메일을 보내는 것을 테스트하려면 [Mail.ru 개발자 문서](https://postmaster.mail.ru/amp/?lang=en#howto)(**사용자** 섹션인 경우)의 단계를 따릅니다.

### 이메일 공급자 {#delivering-amp-emails-by-registering}에 등록하여 AMP 이메일 제공

보낸 사람 도메인을 허용 목록에 추가하기 위해 지원되는 이메일 공급자에 등록하여 동적 이메일 제공을 실험할 수 있습니다.

>[!NOTE]
>
>현재 Gmail, Outlook 및 Mail.ru만 AMP 형식을 지원합니다.

몇 개의 주소로 테스트하고 나면 AMP 이메일을 Gmail 또는 Outlook 주소로 보낼 수 있습니다. 이를 위해서는 구글이나 마이크로소프트에 정중히 등록하고, 그들의 답변을 기다리셔야 합니다. [Gmail](https://developers.google.com/gmail/ampemail/register) 및 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) 개발자 문서에 있는 단계를 따릅니다. 등록이 완료되면 공인 보낸 사람이 됩니다.

AMP 이메일을 Mail.ru 주소로 보내려면 [Mail.ru 개발자 문서](https://postmaster.mail.ru/amp/?lang=en#howto)(**이메일 보낸 사람** 섹션인 경우)에 나열된 요구 사항과 단계를 따르십시오.

## AMP 이메일 {#sending-amp-email} 보내기

AMP 콘텐트와 폴백이 준비되고 호환 대상을 정의한 후에는 평소대로 이메일을 보낼 수 있습니다.

현재 Gmail, Outlook 및 Mail.ru만 특정 조건에서 AMP 형식을 지원합니다. 다른 이메일 공급자의 주소를 타깃팅할 수 있지만 이 이메일 주소는 HTML 또는 일반 텍스트 버전으로 수신됩니다.

>[!IMPORTANT]
>
>이메일에 AMP 내용 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않으면 보낼 수 없습니다.

일치하는 받는 사람의 사서함에 AMP 버전의 이메일이 표시됩니다.

예를 들어 이메일에 제품 목록을 포함시킨 경우 제3자 시스템에서 가격을 편집할 때 받는 사람이 사서함에 있는 이메일을 다시 열 때마다 가격이 자동으로 조정됩니다.

>[!NOTE]
>
>특정 도메인이 AMP 이메일을 수신하지 못하도록 메일 처리 규칙을 만들 수 있습니다. [이메일 형식 관리](../../installation/using/email-deliverability.md#managing-email-formats)를 참조하십시오.
>
>기본적으로 **[!UICONTROL AMP inclusion]** 옵션은 **[!UICONTROL No]**&#x200B;로 설정됩니다.

## 자습서 비디오 {#amp-email-video}

아래 비디오에서는 Adobe Campaign Classic에서 AMP를 활성화하는 방법을 설명하고 사용법을 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
