---
product: campaign
title: Adobe Campaign Classic에서 대화형 콘텐츠 정의
description: Adobe Campaign에서 AMP를 사용하여 인터랙티브하고 다이내믹한 이메일 콘텐츠를 정의하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email Design, Dynamic Content
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 4%

---

# 대화형 콘텐츠 정의{#defining-interactive-content}



Adobe Campaign을 사용하면 대화형 [이메일용 AMP](https://amp.dev/about/email/) 형식 - 특정 조건에서 동적 이메일을 보낼 수 있습니다.

AMP for Email을 사용하면 다음과 같은 작업을 수행할 수 있습니다.
* 적절하게 구성된 특정 주소에 AMP 이메일 전달을 테스트합니다.
* 해당 공급자에 등록한 후 Gmail 또는 Mail.ru 주소로 AMP 이메일을 배달합니다.

AMP 이메일 테스트 및 전송에 대한 자세한 내용은 [이 섹션](#targeting-amp-email).

이 기능은 Adobe Campaign의 전용 패키지를 통해 사용할 수 있습니다. 사용 권한 및 배포 모델에 따라 이 패키지를 설치하거나 Adobe에 연락하여 직접 설치할 수 있습니다.

>[!NOTE]
>
> 하이브리드 및 호스팅 아키텍처의 경우 패키지를 포함하여 모든 서버에 설치해야 합니다. [중간 소싱 서버](../../installation/using/mid-sourcing-server.md) 및 [실행 인스턴스](../../message-center/using/configuring-instances.md#execution-instance).


## AMP for Email 정보 {#about-amp-for-email}

사용 **이메일용 AMP** 메시지에 AMP 구성 요소를 포함하고 풍부하고 실행 가능한 콘텐츠로 이메일 경험을 개선하는 새로운 형식입니다. 이메일 내에서 바로 이용할 수 있는 최신 앱 기능을 통해 수신자는 메시지 자체의 콘텐츠와 동적으로 상호 작용할 수 있습니다.

예제:
* AMP로 작성된 이메일에는 이미지 회전 메뉴 등의 대화형 요소가 포함될 수 있습니다.
* 컨텐츠는 메시지에서 최신 상태로 유지됩니다.
* 수신자는 받은 편지함에서 나가지 않고 양식에 응답할 수 있습니다.

이메일용 AMP는 기존 이메일과 호환됩니다. 메시지의 AMP 버전은 HTML 및/또는 일반 텍스트 외에 새 MIME 부분으로 이메일에 임베드되므로 모든 이메일 클라이언트에서 호환될 수 있습니다.

AMP for Email 형식, 사양 및 요구 사항에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#amp-email-video)

## Adobe Campaign에서 AMP for Email을 사용하는 주요 단계 {#key-steps-to-use-amp}

Adobe Campaign을 사용하여 AMP 이메일을 성공적으로 테스트하고 전송하려면 아래 단계를 따르십시오.
1. 설치 **[!UICONTROL AMP support]** 패키지. 다음을 참조하십시오 [Campaign 기본 제공 패키지 설치](../../installation/using/installing-campaign-standard-packages.md).
1. 이메일을 만들고 Adobe Campaign 내에서 AMP 콘텐츠를 작성합니다. 다음을 참조하십시오 [Adobe Campaign으로 AMP 이메일 콘텐츠 작성](#build-amp-email-content).
1. AMP 형식을 지원하는 이메일 공급자의 모든 게재 요구 사항을 준수해야 합니다. 다음을 참조하십시오 [이메일 게재 요구 사항에 대한 AMP](#amp-for-email-delivery-requirements).
1. 대상을 정의할 때 AMP 형식을 표시할 수 있는 수신자를 선택해야 합니다. 다음을 참조하십시오 [AMP 이메일 타겟팅](#targeting-amp-email).

   >[!NOTE]
   >
   >현재는 AMP 이메일만 게재할 수 있습니다. [특정 이메일 주소](#testing-amp-delivery-for-selected-addresses) (테스트 목적으로) 또는 다음 이후 [등록](#delivering-amp-emails-by-registering) (지원되는 이메일 클라이언트 포함)

1. 평소대로 이메일을 보냅니다. 다음을 참조하십시오 [AMP 이메일 보내기](#sending-amp-email).

## Adobe Campaign에서 AMP 이메일 콘텐츠 작성 {#build-amp-email-content}

AMP 형식을 사용하여 이메일을 작성하려면 아래 단계를 따르십시오.

>[!IMPORTANT]
>
>에 자세히 나와 있는 이메일 요구 사항 및 사양에 대한 AMP를 따라야 합니다. [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). 다음 항목도 확인할 수 있습니다. [AMP for Email 우수 사례](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. 이메일 게재를 만들 때 템플릿을 선택합니다.

   >[!NOTE]
   >
   >특정 AMP 템플릿에는 제품 목록, 회전 메뉴, 이중 옵트인, 설문 조사 및 고급 서버 요청과 같이 사용할 수 있는 주요 기능의 예가 포함되어 있습니다.

1. 다음을 클릭합니다. **[!UICONTROL AMP content]** 탭.

   ![](assets/amp_tab.png)

1. 필요에 따라 AMP 콘텐츠를 편집합니다.

   >[!NOTE]
   >
   >첫 번째 AMP 이메일 작성에 대한 자세한 내용은 [AMP 개발자 설명서](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   예를 들어 AMP 템플릿의 제품 목록 구성 요소를 사용하고 서드파티 시스템 또는 Adobe Campaign 내부에서의 제품 목록을 유지 관리할 수 있습니다. 가격 또는 다른 요소를 조정할 때마다 수신자가 사서함에서 전자 메일을 열면 자동으로 반영됩니다.

1. HTML Adobe Campaign에서 일반적으로 수행하는 개인화 필드 및 개인화 블록과 같이 필요에 따라 AMP 콘텐츠를 개인화합니다.

   ![](assets/amp_tab_perso.png)

1. 편집을 완료하고 나면 전체 AMP 컨텐츠를 선택하고 복사하여 [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org) 또는 유사한 웹 사이트입니다.

   >[!NOTE]
   >
   >다음을 선택하십시오. **AMP4 이메일** 을 클릭하여 제품에서 사용할 수 있습니다.

   ![](assets/amp_validator.png)

   오류는 인라인으로 플래그가 지정됩니다.

   >[!NOTE]
   >
   >Adobe Campaign AMP 편집기는 컨텐츠 유효성 검사를 위해 디자인되지 않았습니다. 다음과 같은 외부 웹 사이트 사용 [AMP 웹 기반 유효성 검사기](https://validator.ampproject.org) 컨텐츠가 올바른지 확인합니다.

1. AMP 콘텐츠가 유효성 검사를 통과할 때까지 필요에 따라 수정하십시오.

   ![](assets/amp_validator_pass.png)

1. 콘텐츠를 미리 보려면 유효성이 확인된 콘텐츠를에 복사-붙여넣습니다. [AMP 플레이그라운드](https://playground.amp.dev) 또는 유사한 웹 사이트입니다.

   >[!NOTE]
   >
   >다음을 선택하십시오. **이메일용 AMP** 을 클릭하여 제품에서 사용할 수 있습니다.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Adobe Campaign에서 직접 AMP 콘텐츠를 미리 볼 수는 없습니다. 다음과 같은 외부 웹 사이트 사용 [AMP 플레이그라운드](https://playground.amp.dev).

1. Adobe Campaign으로 돌아가서 유효성이 확인된 콘텐츠를 **[!UICONTROL AMP content]** 탭.

1. 다음으로 전환 **[!UICONTROL HTML content]** 또는 **[!UICONTROL Text content]** 두 형식 중 하나 이상에 대해 컨텐츠를 탭하고 정의합니다.

   >[!IMPORTANT]
   >
   >이메일에 AMP 콘텐츠 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않으면 전송할 수 없습니다.

## 이메일 게재 요구 사항에 대한 AMP {#amp-for-email-delivery-requirements}

Adobe Campaign에서 AMP 콘텐츠를 작성하는 경우 다이내믹 이메일이 게재되는 조건을 준수해야 하며 다이내믹 이메일은 수신자의 이메일 공급자에 따라 다릅니다.

현재 Gmail 및 Mail.ru의 두 이메일 공급자가 이 형식 테스트를 지원합니다.

Gmail 계정에서 AMP 형식으로 게재를 테스트하는 데 필요한 모든 단계 및 사양은 해당 섹션에 자세히 설명되어 있습니다 [Gmail](https://developers.google.com/gmail/ampemail?), 및 [Mail.ru](https://postmaster.mail.ru/amp) 개발자 설명서.

특히 다음 요구 사항을 충족해야 합니다.
* 다음의 AMP 보안 요구 사항 준수 [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), 및 [Mail.ru](https://postmaster.mail.ru/amp/#howto).
* AMP MIME 부분에는 [유효한 AMP 문서](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* AMP MIME 부분은 100KB보다 작아야 합니다.

다음 항목도 확인할 수 있습니다. [Gmail에 대한 팁 및 알려진 제한 사항](https://developers.google.com/gmail/ampemail/tips) 설명서를 참조하십시오.

## AMP 이메일 Target {#targeting-amp-email}

현재 다음 두 단계로 AMP 이메일 전송을 실험할 수 있습니다.

1. Adobe Campaign을 사용하면 콘텐츠 및 동작을 확인하기 위해 적절하게 구성된 선택한 이메일 주소에 AMP 기반의 동적 이메일을 전달하는 것을 테스트할 수 있습니다. 다음을 참조하십시오 [선택한 주소에 대한 AMP 이메일 게재 테스트](#testing-amp-delivery-for-selected-addresses).

1. 테스트가 완료되면, 관련 이메일 공급업체에 등록하여 허용 목록에 추가하다에 보낸 사람 도메인을 추가하여 이메일 프로그램용 AMP의 일부로 게재 또는 캠페인을 보낼 수 있습니다. 다음을 참조하십시오 [이메일 공급자에 등록하여 AMP 이메일 게재](#delivering-amp-emails-by-registering).

### 선택한 주소에 대한 AMP 이메일 게재 테스트 {#testing-amp-delivery-for-selected-addresses}

Adobe Campaign에서 선택한 이메일 주소로 동적 메시지를 전송하는 것을 테스트할 수 있습니다.

>[!NOTE]
>
>Gmail 및 Mail.ru만 AMP 형식 테스트를 지원합니다.

Gmail의 경우 먼저 타깃팅하는 Adobe Campaign 계정의 Gmail을 전달하기 위해 사용하는 발신자 주소를 허용 목록에 추가하다에 추가해야 합니다.

방법은 다음과 같습니다.
1. 관련 이메일 공급자에 대해 동적 이메일 활성화 옵션이 선택되어 있는지 확인하십시오.
1. 게재에 표시된 발신자 주소를 복사합니다. **[!UICONTROL From]** 필드를 작성하여 이메일 공급자 계정 설정의 해당 섹션에 붙여넣습니다.

자세한 내용은 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 개발자 설명서.

![](assets/amp_from_field.png)

Mail.ru 주소로 AMP 이메일 전송을 테스트하려면 [Mail.ru 개발자 설명서](https://postmaster.mail.ru/amp/#howto) (**사용자인 경우** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

### 이메일 공급자에 등록하여 AMP 이메일 게재 {#delivering-amp-emails-by-registering}

보낸 사람 도메인이 허용 목록에 추가하다에 추가되도록 지원되는 이메일 공급자에 등록하여 다이내믹 이메일 배달을 실험해 볼 수 있습니다.

>[!NOTE]
>
>Gmail 및 Mail.ru만 AMP 형식을 지원합니다.

몇 개의 주소로 테스트한 후에는 모든 Gmail 주소로 AMP 이메일을 보낼 수 있습니다. 이렇게 하려면 Google에 등록하고 답변을 기다려야 합니다. 다음에 제시된 단계를 따릅니다. [Gmail](https://developers.google.com/gmail/ampemail/register) 개발자 설명서. 등록이 완료되면 권한이 있는 발신자가 됩니다.

AMP 이메일을 Mail.ru 주소로 전송하려면 [Mail.ru 개발자 설명서](https://postmaster.mail.ru/amp/#howto) (**이메일 발신자인 경우** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

## AMP 이메일 보내기 {#sending-amp-email}

AMP 콘텐츠와 대체 항목이 준비되고 호환되는 타겟을 정의하면 일반적인 방법으로 이메일을 전송할 수 있습니다.

현재 특정 조건에서 Gmail 및 Mail.ru만 AMP 형식을 지원합니다. 다른 이메일 공급자의 주소를 타겟팅할 수 있지만, 이메일 HTML 또는 일반 텍스트 버전을 받게 됩니다.

>[!IMPORTANT]
>
>이메일에 AMP 콘텐츠 외에 HTML 또는 일반 텍스트 버전이 포함되어 있지 않으면 전송할 수 없습니다.

일치하는 수신자는 사서함에 이메일의 AMP 버전이 표시됩니다.

예를 들어 이메일에 제품 목록을 포함한 경우 서드파티 시스템에서 가격을 편집할 때 수신자가 사서함에서 이메일을 다시 열 때마다 가격이 자동으로 조정됩니다.

>[!NOTE]
>
>특정 도메인이 AMP 이메일을 수신하지 못하도록 메일 처리 규칙을 만들 수 있습니다. 다음을 참조하십시오 [이메일 형식 관리](../../installation/using/email-deliverability.md#managing-email-formats).
>
>기본적으로 **[!UICONTROL AMP inclusion]** 옵션이 로 설정되어 있습니다. **[!UICONTROL No]**.

## 튜토리얼 비디오 {#amp-email-video}

아래 비디오에서는 Adobe Campaign에서 AMP를 활성화하는 방법을 설명하고 사용 사례를 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

추가 캠페인 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
