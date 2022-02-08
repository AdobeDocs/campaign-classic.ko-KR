---
product: campaign
title: Adobe Campaign Classic에서 대화형 콘텐츠 정의
description: Adobe Campaign에서 AMP를 사용하여 인터랙티브하고 다이내믹한 이메일 콘텐츠를 정의하는 방법을 알아봅니다
feature: Email Design, Dynamic Content
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 3%

---

# 대화형 콘텐츠 정의{#defining-interactive-content}

![](../../assets/common.svg)

Adobe Campaign을 사용하면 새로운 대화형 기능을 사용할 수 있습니다 [이메일용 AMP](https://amp.dev/about/email/) 특정 조건에서 다이내믹 이메일을 보낼 수 있는 형식입니다.

AMP for Email을 사용하면 다음 작업을 수행할 수 있습니다.
* 적절하게 구성된 특정 주소에 AMP 이메일 전달을 테스트합니다.
* 해당 공급자에 등록한 후 Gmail, Outlook 또는 Mail.ru 주소로 AMP 이메일을 배달합니다.

AMP 이메일 테스트 및 전송에 대한 자세한 내용은 [이 섹션](#targeting-amp-email).

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용 권한 및 배포 모델에 따라 이 패키지를 설치하거나 Adobe에 연락하여 설치할 수 있습니다.

>[!NOTE]
>
> 하이브리드 및 호스팅 아키텍처의 경우 패키지를 포함하여 모든 서버에 설치해야 합니다 [중간 소싱 서버](../../installation/using/mid-sourcing-server.md) 그리고 [실행 인스턴스](../../message-center/using/configuring-instances.md#execution-instance).


## AMP for Email 정보 {#about-amp-for-email}

를 사용하십시오 **이메일용 AMP** 메시지에 AMP 구성 요소를 포함하고 실행 가능한 풍부한 콘텐츠를 사용하여 이메일 경험을 개선하는 새로운 형식입니다. 이메일 내에서 바로 이용할 수 있는 최신 앱 기능을 통해 수신자는 메시지 자체의 콘텐츠와 동적으로 상호 작용할 수 있습니다.

예제:
* AMP로 작성된 이메일에는 이미지 회전 슬라이드와 같은 대화형 요소가 포함될 수 있습니다.
* 메시지가 최신 상태로 유지됩니다.
* 수신자는 받은 편지함을 벗어나지 않고 양식에 응답할 수 있습니다.

이메일용 AMP는 기존 이메일과 호환됩니다. 메시지의 AMP 버전은 HTML 및/또는 일반 텍스트 외에 새로운 MIME 부분으로 전자 메일에 포함되므로 모든 이메일 클라이언트와의 호환성을 보장합니다.

전자 메일 형식, 사양 및 요구 사항에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#amp-email-video)

## Adobe Campaign에서 이메일에 AMP를 사용하는 주요 단계 {#key-steps-to-use-amp}

Adobe Campaign을 사용하여 AMP 이메일을 성공적으로 테스트하고 전송하려면 아래 단계를 따르십시오.
1. 설치 **[!UICONTROL AMP support]** 패키지. 자세한 내용은 [Campaign 기본 제공 패키지 설치](../../installation/using/installing-campaign-standard-packages.md).
1. Adobe Campaign 내에서 이메일을 만들고 AMP 콘텐츠를 빌드합니다. 자세한 내용은 [Adobe Campaign을 사용하여 AMP 이메일 콘텐츠 제작](#build-amp-email-content).
1. AMP 형식을 지원하는 이메일 공급자의 모든 게재 요구 사항을 따라야 합니다. 자세한 내용은 [전자 메일 게재 요구 사항용 AMP](#amp-for-email-delivery-requirements).
1. 대상을 정의할 때 AMP 형식을 표시할 수 있는 수신자를 선택해야 합니다. 자세한 내용은 [AMP 이메일 타겟팅](#targeting-amp-email).

   >[!NOTE]
   >
   >현재는 AMP 이메일만 게재할 수 있습니다 [특정 이메일 주소](#testing-amp-delivery-for-selected-addresses) (테스트 목적) 또는 이후 [등록](#delivering-amp-emails-by-registering) 지원되는 이메일 클라이언트 사용.

1. 평소대로 이메일을 보내십시오. 자세한 내용은 [AMP 이메일 보내기](#sending-amp-email).

## Adobe Campaign에서 AMP 이메일 콘텐츠 작성 {#build-amp-email-content}

AMP 형식을 사용하여 이메일을 작성하려면 아래 단계를 따르십시오.

>[!IMPORTANT]
>
>AMP for Email 요구 사항 및 세부 사항은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). 또한 [AMP for Email 우수 사례](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. 이메일 게재를 만들 때 템플릿을 선택합니다.

   >[!NOTE]
   >
   >특정 AMP 템플릿에는 사용할 수 있는 기본 기능의 예가 포함되어 있습니다. 제품 목록, 회전 메뉴, 이중 옵트인, 설문 조사 및 고급 서버 요청.

1. 을(를) 클릭합니다. **[!UICONTROL AMP content]** 탭.

   ![](assets/amp_tab.png)

1. 필요에 따라 AMP 컨텐츠를 편집합니다.

   >[!NOTE]
   >
   >첫 번째 AMP 이메일 빌드에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   예를 들어 AMP 템플릿의 제품 목록 구성 요소를 사용하고 타사 시스템 또는 Adobe Campaign 내부에서도 제품 목록을 유지할 수 있습니다. 가격 또는 다른 요소를 조정할 때마다 수신자가 사서함에서 이메일을 열 때 자동으로 반영됩니다.

1. 개인화 필드 및 개인화 블록을 사용하여, 일반적으로 Adobe Campaign의 HTML 포맷과 하듯이 필요에 따라 AMP 콘텐츠를 개인화합니다.

   ![](assets/amp_tab_perso.png)

1. 편집을 완료했으면 전체 AMP 컨텐츠를 선택하고 을(를) 복사하여 [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org) 또는 유사한 웹 사이트입니다.

   >[!NOTE]
   >
   >다음을 선택해야 합니다 **AMP4 이메일** 화면 상단의 드롭다운 목록에서 를 클릭합니다.

   ![](assets/amp_validator.png)

   오류에 인라인 플래그가 지정됩니다.

   >[!NOTE]
   >
   >Adobe Campaign AMP 편집기는 콘텐츠 유효성 검사를 위해 설계되지 않았습니다. 와 같은 외부 웹 사이트 사용 [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org) 컨텐츠가 올바른지 확인합니다.

1. AMP 컨텐츠가 유효성 검사를 통과할 때까지 필요에 따라 수정합니다.

   ![](assets/amp_validator_pass.png)

1. 콘텐츠를 미리 보려면 유효성 검사된 콘텐츠를 [AMP 놀이터](https://playground.amp.dev) 또는 유사한 웹 사이트입니다.

   >[!NOTE]
   >
   >다음을 선택해야 합니다 **이메일용 AMP** 화면 상단의 드롭다운 목록에서 를 클릭합니다.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Adobe Campaign에서 직접 AMP 컨텐츠를 미리 볼 수 없습니다. 다음과 같은 외부 웹 사이트 사용 [AMP 놀이터](https://playground.amp.dev).

1. Adobe Campaign으로 돌아가서 유효성 검사된 컨텐츠를 에 복사하여 붙여넣습니다 **[!UICONTROL AMP content]** 탭.

1. 로 전환 **[!UICONTROL HTML content]** 또는 **[!UICONTROL Text content]** 탭하여 이 두 형식 중 적어도 하나에 대한 콘텐츠를 정의합니다.

   >[!IMPORTANT]
   >
   >이메일에 AMP 콘텐츠 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않다면 보낼 수 없습니다.

## 전자 메일 게재 요구 사항용 AMP {#amp-for-email-delivery-requirements}

Adobe Campaign에서 AMP 콘텐츠를 작성할 때에는 수신자의 이메일 공급자에 특정한 다이내믹 이메일을 배달하기 위한 조건을 준수해야 합니다.

현재 세 개의 이메일 공급자가 이 형식 테스트를 지원합니다. Gmail, Outlook 및 Mail.ru.

Gmail 계정에서 AMP 포맷으로 게재를 테스트하는 데 필요한 모든 단계 및 사양은 해당 항목에 자세히 설명되어 있습니다 [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/), 및 [Mail.ru](https://postmaster.mail.ru/amp) 개발자 설명서.

특히 다음 요구 사항을 충족해야 합니다.
* 다음의 특정 AMP 보안 요구 사항을 따르십시오 [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements), 및 [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* AMP MIME 부분에는 [유효한 AMP 문서](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* AMP MIME 부분은 100KB보다 작아야 합니다.

또한 [Gmail의 팁 및 알려진 제한 사항](https://developers.google.com/gmail/ampemail/tips) 그리고 [Outlook용 AMP 우수 사례](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## AMP 이메일 Target {#targeting-amp-email}

현재 AMP 이메일 전송을 두 단계로 실험할 수 있습니다.

1. Adobe Campaign을 사용하면 콘텐츠 및 동작을 확인하기 위해 적절하게 구성된 선택한 이메일 주소로 AMP 기반 다이내믹 이메일을 전달하는 것을 테스트할 수 있습니다. 자세한 내용은 [선택한 주소에 대한 AMP 이메일 게재 테스트](#testing-amp-delivery-for-selected-addresses).

1. 테스트가 완료되면, 관련 이메일 공급자에 등록하여 발신자 도메인을에 추가하도록 함으로써 게재 또는 캠페인을 이메일 프로그램용 AMP 프로그램의 일부로 보낼 수 허용 목록에 추가하다 있습니다. 자세한 내용은 [이메일 공급자에 등록하여 AMP 이메일 게재](#delivering-amp-emails-by-registering).

### 선택한 주소에 대한 AMP 이메일 게재 테스트 {#testing-amp-delivery-for-selected-addresses}

Adobe Campaign에서 선택한 이메일 주소로 동적 메시지 전송을 테스트할 수 있습니다.

>[!NOTE]
>
>현재 Gmail, Outlook 및 Mail.ru만 AMP 형식 테스트를 지원합니다.

Gmail 및 Outlook의 경우 먼저 타깃팅하는 Gmail 및 Outlook 계정에 대해 Adobe Campaign에서 허용 목록에 추가하다 게재하기 위해에 사용하는 발신자 주소를 추가해야 합니다.

방법은 다음과 같습니다.
1. 관련 이메일 공급자에 대해 다이내믹 이메일 활성화 옵션이 선택되어 있는지 확인합니다.
1. 게재 주소에 표시되는 발신자 주소 복사 **[!UICONTROL From]** 필드를 만들어 전자 메일 공급자 계정 설정의 해당 섹션에 붙여넣습니다.

자세한 내용은 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 및 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) 개발자 설명서.

![](assets/amp_from_field.png)

Mail.ru 주소로 AMP 이메일 전송을 테스트하려면 [Mail.ru 개발자 설명서](https://postmaster.mail.ru/amp/?lang=en#howto) (**사용자인 경우** 섹션).

### 이메일 공급자에 등록하여 AMP 이메일 게재 {#delivering-amp-emails-by-registering}

발신자 도메인을에 추가하기 위해 지원되는 이메일 공급자에 등록하여 동적 이메일 게재를 실험할 수 허용 목록에 추가하다 있습니다.

>[!NOTE]
>
>현재 Gmail, Outlook 및 Mail.ru만 AMP 형식을 지원합니다.

몇 개의 주소로 테스트한 후에는 모든 Gmail 또는 Outlook 주소로 AMP 이메일을 보낼 수 있습니다. 이를 위해서는 Google 또는 Microsoft에 정중히 등록하고 이들의 응답을 기다려야 합니다. 에 제시된 단계를 따르십시오. [Gmail](https://developers.google.com/gmail/ampemail/register) 및 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) 개발자 설명서. 등록 성공 후 인증된 보낸 사람이 됩니다.

AMP 이메일을 Mail.ru 주소로 보내려면 [Mail.ru 개발자 설명서](https://postmaster.mail.ru/amp/?lang=en#howto) (**이메일 발신자인 경우** 섹션).

## AMP 이메일 보내기 {#sending-amp-email}

AMP 콘텐츠 및 폴백이 준비되고, 호환 타겟을 정의했으면 평소대로 이메일을 보낼 수 있습니다.

현재 Gmail, Outlook 및 Mail.ru만 특정 조건에서 AMP 형식을 지원합니다. 다른 이메일 공급자를 통해 주소를 타겟팅할 수 있지만, 이메일 HTML 또는 일반 텍스트 버전을 수신합니다.

>[!IMPORTANT]
>
>이메일에 AMP 콘텐츠 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않다면 보낼 수 없습니다.

일치하는 수신자는 AMP 버전의 이메일이 사서함에 표시됩니다.

예를 들어, 이메일에 제품 목록을 포함한 경우, 타사 시스템에서 가격을 편집할 때 수신자가 사서함에서 이메일을 다시 열 때마다 가격이 자동으로 조정됩니다.

>[!NOTE]
>
>특정 도메인이 AMP 이메일을 받지 못하도록 하는 메일 처리 규칙을 만들 수 있습니다. 자세한 내용은 [이메일 형식 관리](../../installation/using/email-deliverability.md#managing-email-formats).
>
>기본적으로 **[!UICONTROL AMP inclusion]** 옵션이 **[!UICONTROL No]**.

## 튜토리얼 비디오 {#amp-email-video}

아래 비디오에서는 Adobe Campaign에서 AMP를 활성화하는 방법을 설명하고 사용 사례를 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

추가 Campaign 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
