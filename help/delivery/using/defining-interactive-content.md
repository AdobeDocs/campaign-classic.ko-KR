---
title: Adobe Campaign Classic에서 인터랙티브한 컨텐츠 정의
description: Adobe Campaign Classic에서 AMP를 사용하여 인터랙티브하고 다이내믹한 이메일 컨텐츠를 정의하는 방법을 살펴볼 수 있습니다.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a636d56652e1045e7c48bd2e1a2420b58212739a
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 3%

---


# 대화형 콘텐츠 정의{#defining-interactive-content}

Adobe Campaign을 사용하면 특정 조건 [에서 동적 이메일을 보낼 수 있는 새로운 대화형](https://amp.dev/about/email/) AMP for Email 형식을 사용할 수 있습니다.

현재 이메일용 AMP가 있는 경우 다음을 수행할 수 있습니다.
* 적절하게 구성된 특정 주소에 AMP 이메일 전달을 테스트합니다.
* 해당 공급자에 등록한 후 AMP 이메일을 Gmail, Outlook 또는 Mail.ru 주소로 배달합니다.

AMP 이메일 테스트 및 전송에 대한 자세한 내용은 AMP 이메일 [타깃팅을 참조하십시오](#targeting-amp-email).

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용하려면 이 패키지를 설치해야 합니다. 완료되면 패키지를 고려하기 위해 서버를 다시 시작합니다.

>[!NOTE]
>
> 하이브리드 및 호스팅 아키텍처의 경우 [중간 소싱 서버](../../installation/using/mid-sourcing-server.md) 및 [실행 인스턴스](../../message-center/using/creating-a-shared-connection.md#execution-instance)등 모든 서버에 패키지를 설치해야 합니다. 계정 담당자에게 문의하십시오.

## 이메일의 AMP 정보 {#about-amp-for-email}

이메일용 **AMP** 새로운 포맷을 사용하면 메시지 내에 AMP 구성 요소를 포함할 수 있으므로 풍부하고 실행 가능한 컨텐츠로 이메일 경험을 향상시킬 수 있습니다. 이메일 내에서 바로 이용할 수 있는 최신 앱 기능을 통해 수신자는 메시지 자체의 콘텐츠와 동적으로 상호 작용할 수 있습니다.

예제:
* AMP로 작성된 이메일에는 이미지 Carousel과 같은 대화형 요소가 포함될 수 있습니다.
* 메시지의 콘텐츠가 최신 상태로 유지됩니다.
* 수신자는 받은 편지함을 그대로 두고 양식에 응답하는 등의 조치를 취할 수 있습니다.

이메일용 AMP는 기존 이메일과 호환됩니다. 메시지의 AMP 버전은 HTML 및/또는 일반 텍스트 외에 새로운 MIME 부분으로 이메일에 포함되므로 모든 이메일 클라이언트에서 호환성이 보장됩니다.

이메일 포맷, 사양 및 요구 사항에 대한 AMP에 대한 자세한 내용은 [AMP 개발자 설명서를 참조하십시오](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#amp-email-video)

## Adobe Campaign에서 이메일에 AMP를 사용하는 주요 단계 {#key-steps-to-use-amp}

Adobe Campaign과 함께 AMP 이메일을 성공적으로 테스트 및 전송하려면 아래 단계를 따르십시오.
1. 패키지를 **[!UICONTROL AMP support]** 설치합니다. Campaign [표준 패키지 설치를 참조하십시오](../../installation/using/installing-campaign-standard-packages.md).
1. Adobe Campaign에서 이메일을 만들어 AMP 콘텐츠를 제작할 수 있습니다. Adobe Campaign [를 사용하여 AMP 이메일 콘텐츠 제작을 참조하십시오](#build-amp-email-content).
1. AMP 형식을 지원하는 이메일 제공업체의 모든 전달 요구 사항을 따라야 합니다. 이메일 [전달 요구 사항은 AMP를 참조하십시오](#amp-for-email-delivery-requirements).
1. 대상을 정의할 때 AMP 형식을 표시할 수 있는 수신자를 선택해야 합니다. AMP [이메일 타깃팅을 참조하십시오](#targeting-amp-email).

   >[!NOTE]
   >
   >현재 AMP 이메일은 [특정 이메일 주소](#testing-amp-delivery-for-selected-addresses) (테스트 목적) 또는 지원되는 이메일 클라이언트에 [등록한](#delivering-amp-emails-by-registering) 후에만 전달할 수 있습니다.

1. 평상시처럼 이메일 전송 AMP [이메일 전송을 참조하십시오](#sending-amp-email).

## Adobe Campaign에서 AMP 이메일 컨텐츠 제작 {#build-amp-email-content}

AMP 형식을 사용하여 이메일을 작성하려면 아래 단계를 따르십시오.

>[!IMPORTANT]
>
>AMP 개발자 설명서에 나와 있는 이메일 요구 사항 및 사양에 대한 AMP를 [따라야 합니다](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). AMP에서 이메일 [모범 사례를 참조할 수도 있습니다](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. 이메일 배달을 만들 때 템플릿을 선택합니다.

   >[!NOTE]
   >
   >특정 AMP 템플릿에는 사용할 수 있는 기본 용량 예제가 포함되어 있습니다.제품 목록, 회전판, 이중 옵트인, 설문 조사 및 고급 서버 요청

1. 탭을 **[!UICONTROL AMP content]** 클릭합니다.

   ![](assets/amp_tab.png)

1. 요구 사항에 맞게 AMP 컨텐츠를 편집할 수 있습니다.

   >[!NOTE]
   >
   >첫 번째 AMP 이메일 작성에 대한 자세한 내용은 [AMP 개발자 설명서를 참조하십시오](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   예를 들어 AMP 템플릿의 제품 목록 구성 요소를 사용하고 타사 시스템 또는 Adobe Campaign 내부 제품 목록을 유지할 수 있습니다. 가격이나 다른 요소를 조정할 때마다 받는 사람이 사서함에서 이메일을 다시 열면 자동으로 반영됩니다.

1. 개인화 필드 및 개인화 블록을 통해 Adobe Campaign의 HTML 포맷에서와 같이 필요에 따라 AMP 컨텐츠를 개인화할 수 있습니다.

   ![](assets/amp_tab_perso.png)

1. 편집을 완료한 후 전체 AMP 컨텐츠를 선택하고 [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org) 또는 유사한 웹 사이트에 복사하여 붙여넣습니다.

   >[!NOTE]
   >
   >화면 상단의 **드롭다운 목록에서 AMP4** EMAIL을 선택해야 합니다.

   ![](assets/amp_validator.png)

   오류가 인라인으로 플래그가 지정됩니다.

   >[!NOTE]
   >
   >Adobe Campaign AMP 편집기는 콘텐츠 유효성 검사를 위해 디자인되지 않았습니다. AMP 웹 기반 유효성 검사기와 같은 외부 웹 사이트 [를](https://validator.ampproject.org) 사용하여 내용이 올바른지 확인하십시오.

1. AMP 컨텐츠가 유효성 검사를 통과하기 전까지 필요에 따라 수정합니다.

   ![](assets/amp_validator_pass.png)

1. 검증된 컨텐츠를 AMP [Playground](https://playground.amp.dev) 또는 유사한 웹 사이트에 복사하여 붙여넣으면 컨텐츠를 미리 볼 수 있습니다.

   >[!NOTE]
   >
   >화면 상단에 있는 **드롭다운 목록에서 이메일에** 대한 AMP를 선택해야 합니다.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Adobe Campaign에서 직접 AMP 콘텐츠를 미리 볼 수는 없습니다. AMP 놀이터와 같은 외부 웹 [사이트를 사용합니다](https://playground.amp.dev).

1. Adobe Campaign으로 돌아가 유효성이 확인된 컨텐츠를 복사하여 **[!UICONTROL AMP content]** 탭에 붙여넣습니다.

1. 또는 **[!UICONTROL HTML content]** 탭으로 **[!UICONTROL Text content]** 전환하고 이러한 두 형식 중 적어도 하나에 대한 내용을 정의합니다.

   >[!IMPORTANT]
   >
   >이메일에 AMP 컨텐츠 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않으면 보낼 수 없습니다.

## 이메일 전달 요구 사항에 대한 AMP {#amp-for-email-delivery-requirements}

Adobe Campaign에서 AMP 컨텐츠를 빌드할 때는 수신자의 이메일 공급자에 따라 제공되는 동적 이메일의 조건을 준수해야 합니다.

현재 세 개의 이메일 제공업체에서 이 형식을 테스트하는 것을 지원합니다.Gmail, Outlook 및 Mail.ru.

Gmail 계정에서 AMP 포맷으로 전달할 내용을 테스트하는 데 필요한 모든 단계 및 사양은 해당 [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) 및 [Mail.ru](https://postmaster.mail.ru/amp) 개발자 문서에 자세히 설명되어 있습니다.

특히 다음 요구 사항을 충족해야 합니다.
* Gmail, [Outlook](https://developers.google.com/gmail/ampemail/security-requirements)및 [Mail](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) .ru와 관련된 AMP 보안 요구 사항을 [따르십시오](https://postmaster.mail.ru/amp/?lang=en#howto).
* AMP MIME 부분에 [유효한 AMP 문서가 있어야 합니다](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* AMP MIME 부분은 100KB보다 작아야 합니다.

Gmail에 대한 [팁과 알려진 제한 사항](https://developers.google.com/gmail/ampemail/tips) 및 Outlook [에 대한 AMP 우수 사례를 참조할 수도 있습니다](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## AMP 이메일 타깃팅 {#targeting-amp-email}

현재 AMP 이메일 전송을 두 단계로 실험해 볼 수 있습니다.

1. Adobe Campaign을 사용하면 컨텐츠와 동작을 확인하기 위해 AMP 기반의 동적 이메일을 선택한 이메일 주소로 적절하게 구성된 것을 테스트할 수 있습니다. 선택한 [주소에 대한 AMP 이메일 배달 테스트를 참조하십시오](#testing-amp-delivery-for-selected-addresses).
1. 테스트를 거친 후에는 해당 이메일 공급자에 등록하여 보낸 사람 도메인을 허용 목록에 추가하도록 함으로써 이메일용 AMP 프로그램의 일부로 게재 또는 캠페인을 보낼 수 있습니다. 이메일 [공급자에 등록하여 AMP 이메일 전달을 참조하십시오](#delivering-amp-emails-by-registering).

### 선택한 주소에 대한 AMP 이메일 배달 테스트 {#testing-amp-delivery-for-selected-addresses}

Adobe Campaign에서 선택한 이메일 주소로 동적 메시지 전송을 테스트할 수 있습니다.

>[!NOTE]
>
>현재 Gmail, Outlook 및 Mail.ru만 AMP 형식 테스트를 지원합니다.

Gmail 및 Outlook의 경우, 먼저 대상 Gmail 및 Outlook 계정에 대해 Adobe Campaign에서 배달하기 위해 허용 목록에 사용 중인 보낸 사람 주소를 추가해야 합니다.

방법은 다음과 같습니다.
1. 관련 이메일 공급자에 대해 동적 이메일 활성화 옵션이 선택되어 있는지 확인합니다.
1. 배달 필드에 표시된 보낸 사람 주소를 복사하여 이메일 공급자 계정 설정의 **[!UICONTROL From]** 해당 섹션에 붙여 넣습니다.

자세한 내용은 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 및 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) 개발자 설명서를 참조하십시오.

![](assets/amp_from_field.png)

Mail.ru 주소로 AMP 이메일 전송을 테스트하려면 [Mail.ru 개발자 문서](https://postmaster.mail.ru/amp/?lang=en#howto) (사용자&#x200B;**의 경우)의 단계를** 따릅니다.

### 이메일 공급자에 등록하여 AMP 이메일 전달 {#delivering-amp-emails-by-registering}

보낸 사람 도메인을 허용 목록에 추가하기 위해 지원되는 이메일 공급자에 등록하여 동적 이메일 제공을 실험할 수 있습니다.

>[!NOTE]
>
>현재 Gmail, Outlook 및 Mail.ru만 AMP 형식을 지원합니다.

몇 개의 주소로 테스트한 후에는 AMP 이메일을 Gmail 또는 Outlook 주소로 보낼 수 있습니다. 이를 위해서는 구글이나 마이크로소프트에 정중하게 등록해야 하며 이들의 답변을 기다리고 있어야 합니다. Gmail 및 [Outlook](https://developers.google.com/gmail/ampemail/register) 개발자 문서에 나와 있는 [단계를](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) 따릅니다. 등록이 완료되면 공인 보낸 사람이 됩니다.

AMP 이메일을 Mail.ru 주소로 전송하려면 [Mail.ru 개발자 설명서에 나와 있는 요구 사항 및 단계](https://postmaster.mail.ru/amp/?lang=en#howto) (**이메일 발신자** 섹션인 경우)를 따르십시오.

## AMP 이메일 보내기 {#sending-amp-email}

AMP 컨텐츠와 폴백이 준비되고, 호환 타겟을 정의한 후에는 평소대로 이메일을 보낼 수 있습니다.

현재 Gmail, Outlook 및 Mail.ru만 특정 조건에서 AMP 형식을 지원합니다. 다른 이메일 공급자의 주소를 타깃팅할 수 있지만 이메일 HTML이나 일반 텍스트 버전을 받게 됩니다.

>[!IMPORTANT]
>
>이메일에 AMP 컨텐츠 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않으면 보낼 수 없습니다.

일치하는 받는 사람의 AMP 버전의 이메일이 사서함에 표시됩니다.

예를 들어 이메일에 제품 목록을 포함시킨 경우 타사 시스템에서 가격을 편집할 때 받는 사람이 자신의 사서함에서 이메일을 다시 열 때마다 가격이 자동으로 조정됩니다.

>[!NOTE]
>
>특정 도메인이 AMP 이메일을 수신하지 못하도록 메일 처리 규칙을 만들 수 있습니다. 이메일 [형식 관리를 참조하십시오](../../installation/using/email-deliverability.md#managing-email-formats).
>
>기본적으로 이 **[!UICONTROL AMP inclusion]** 옵션은 로 설정됩니다 **[!UICONTROL No]**.

## 이메일에 AMP를 활성화하고 사용하는 방법 {#amp-email-video}

아래 비디오에서는 Adobe Campaign Classic에서 AMP를 활성화하는 방법을 설명하고 사용법을 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)
