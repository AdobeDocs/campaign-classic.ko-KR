---
title: 개인화된 콘텐츠 제작
seo-title: 개인화된 콘텐츠 제작
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c804745ae58a9bded885ac5aef32f019f43e82be
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 7%

---


# 개인화된 콘텐츠 제작 {#build-personalized-content}

메시지 내용을 디자인할 때 배달 실행을 방지할 수 있는 일반적인 문제를 방지하십시오. 대부분의 경우 [개인화](../../delivery/using/about-personalization.md), 서식 [및](../../delivery/using/defining-the-email-content.md#message-content) 이미지 [와 관련된 오류가 발생할 수 있습니다](../../delivery/using/defining-the-email-content.md#adding-images).

## 개인화 최적화 {#optimize-personalization}

메시지 전달을 실행하지 못하도록 하고 받는 사람의 경험을 향상시킬 수 있는 일반적인 문제를 방지하기 위해 Adobe Campaign을 사용하면 메시지를 개인화할 수 있습니다.

Adobe Campaign 데이터베이스에 저장된 수신자 데이터를 사용하거나 추적, 랜딩 페이지, 구독 등을 통해 수집할 수 있습니다.
개인화 기본 사항은 [이 섹션에 나와 있습니다](../../delivery/using/personalization-fields.md).

메시지 컨텐츠가 개인화와 관련된 오류를 방지하도록 제대로 설계되었는지 확인하십시오.

**팁**:타사 공급업체에서 제공한 외부 파일에서 나오는 개인화 필드에서 외부 HTML 콘텐츠가 잘못될 수 있습니다. 이를 방지하려면 구문, 태그, 문자 등의 사용을 확인하십시오. 예를 들어 Adobe Campaign 개인화 태그에는 항상 다음 양식이 있습니다.&lt;%=table.field%>. 자세한 내용은 [이 섹션](../../delivery/using/about-personalization.md)을 참조하십시오.

개인화 블록에서 매개 변수가 잘못 사용될 수 있습니다. 예를 들어 JavaScript의 변수는 다음과 같이 사용해야 합니다.

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

개인화 블록에 대한 자세한 내용은 [이 섹션을 참조하십시오](../../delivery/using/personalization-blocks.md).

워크플로우에서 개인화 데이터를 준비하여 전달 준비 분석을 향상시킬 수 있습니다. 개인화 데이터가 FDA(Federated Data Access)를 통해 외부 테이블에서 가져오는 경우 특별히 사용해야 합니다. 이 옵션은 [이 섹션에 설명되어 있습니다.](../../delivery/using/personalization-fields.md#optimizing-personalization)

## 최적화된 콘텐츠 제작 {#optimize-content}

이메일을 작성할 때 아래의 일반적인 모범 사례를 염두에 두십시오.

* 디자인 간소화

* 모바일 사용자를 염두에 두십시오

* 이미지 기반의 이메일 수신 방지

* 이메일 안전 글꼴 사용

* 특수 문자 인코딩

### 제목

개방률을 [높이기](../../delivery/using/defining-the-email-content.md#message-content) 위해 주제 라인

* 너무 긴 과목은 피하세요. 최대 50자를 사용할 수 있습니다

* 스팸으로 간주될 수 있는 &quot;무료&quot; 또는 &quot;오퍼&quot;와 같은 반복적인 단어를 사용하지 마십시오

* 대문자 및 &quot;!&quot;, &quot; 저녁&quot;, &quot;\&quot;, &quot;$&quot;와 같은 특수 문자를 사용하지 마십시오.

### 미러 페이지

항상 미러 페이지 링크를 포함합니다. 이메일의 맨 위에 기본 위치가 있습니다. [자세히 알아보기](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### 구독 취소 링크

구독 취소 링크는 필수적입니다. 반드시 표시되고 유효해야 하며, 양식이 제대로 작동하는지 확인해야 합니다. 기본적으로 메시지를 분석하면 분류 규칙 [이 옵트아웃 링크](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) 포함 여부를 확인하고 누락된 경우 경고를 생성합니다.

**팁**:사용자 오류는 항상 가능하므로 전송 때마다 옵트아웃 링크가 제대로 작동하는지 확인합니다. 예를 들어 증거를 보낼 때 링크가 유효한지, 양식이 온라인인지, 이 수신자에게 더 이상 연락하지 않음 필드가 예로 변경되었는지 확인하십시오.

이 섹션 [에 옵트아웃 링크를 삽입하는 방법을 알아봅니다](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

### 이메일 크기

성능 또는 전달 문제가 발생하지 않도록 하기 위해 권장되는 최대 이메일 크기는 약 **35KB입니다**. 메시지 크기를 확인하려면 **[!UICONTROL Preview]** 탭으로 이동하여 테스트 프로필을 선택합니다. 메시지 크기가 생성되면 오른쪽 상단 모서리에 표시됩니다.

이메일을 제한된 범위 내에서 유지하려면 다음을 고려하십시오.

* 중복 또는 사용하지 않는 스타일 제거

* 이메일 콘텐츠 중 일부를 랜딩 페이지로 이동

* 코드 축소

최종 전송 전에 변경 사항을 테스트하십시오

### SMS 길이

기본적으로 SMS의 글자 수는 GSM(이동통신 글로벌 시스템) 표준을 충족합니다. GSM 인코딩을 사용하는 SMS 메시지는 SMS당 160자, 또는 여러 부분으로 나누어 전송되는 메시지의 경우 153자로 제한됩니다.

변환은 GSM 표준에서 고려하지 않는 SMS 문자를 다른 문자로 바꾸는 작업입니다. SMS 메시지의 컨텐츠에 개인화 필드를 삽입하면 GSM 인코딩에 의해 고려되지 않는 문자가 도입될 수 있습니다. 해당 채널의 SMPP 채널 설정 탭에서 해당 상자를 선택하여 문자 교환을 인증할 수 있습니다 **[!UICONTROL External account]**.
이 섹션 [에서 자세히 알아보십시오](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**팁**:

* SMS 메시지의 모든 문자를 그대로 유지하려면 적절한 이름을 바꾸지 마십시오. 음역을 활성화하지 마십시오.

* 그러나 GSM 표준으로 간주되지 않는 많은 문자가 SMS 메시지에 포함되어 있는 경우, 교역을 활성화하여 메시지 전송 비용을 제한합니다.

이 섹션 [에서 자세히 알아보십시오](../../delivery/using/sms-channel.md#about-character-transliteration).

## 서식에 대한 작업 {#formatting}

일반적인 서식 오류를 방지하려면 다음 요소를 확인하십시오.

* 올바른 **날짜 서식**:Adobe Campaign은 JavaScript 템플릿 및 XSL 스타일시트에 날짜 서식 기능을 제공합니다. [자세히 알아보기](../../delivery/using/formatting.md#date-display)

* 이메일에서 **인증된 문자** 사용:이메일 주소의 유효한 문자 목록은 &quot;XtkEmail_Characters&quot; 옵션에 정의되어 있습니다. 이 섹션에서 캠페인 옵션 [에 액세스하는 방법을 알아봅니다](../../installation/using/configuring-campaign-options.md). 특수 문자를 올바로 처리하려면 유니코드로 Adobe Campaign을 설치해야 합니다.

* 이메일 **인증 구성**:이메일 헤더에 DKIM 서명이 포함되어 있는지 확인합니다. DKIM(Domain Keys Identified Mail) 인증을 통해 수신 이메일 서버는 메시지를 보낸 것이라고 주장하는 사람 또는 엔티티가 메시지를 실제로 보냈는지, 메시지 컨텐츠가 처음 전송된 시간(및 DKIM &quot;signed&quot;) 및 수신한 시간 사이에 변경되었는지 여부를 확인할 수 있습니다. 이 표준은 일반적으로 보낸 사람 헤더의 도메인을 사용합니다. 자세한 정보는 [이 섹션](../../delivery/using/technical-recommendations.md#dkim)을 참조하십시오.

### 반응형 이메일 디자인

반응형 디자인을 사용하면 이메일이 열려 있는 장치에 맞게 최적으로 렌더링됩니다.

* 웹 HTML이 아닌 반응형 이메일 HTML 사용

* 미리 보기 모드를 사용하여 가능한 한 많은 디바이스에서 렌더링을 테스트할 수 있는 교정본을 전송합니다

* Adobe Campaign Classic DCE(Digital Content Editor) 모듈에는 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** 를 통해 사용할 수 있는 모바일용 반응형 디자인 형식 템플릿이 포함되어 있습니다 **[!UICONTROL Content templates]**. 이 문서 [의 자세한 내용](https://theblog.adobe.com/responsive-email-design-101/)

## 이미지 관리 {#manage-images}

이미지 사용에 대해서는 아래 지침을 따르십시오.

### 이미지 차단 방지

일부 이메일 클라이언트는 기본적으로 이미지를 차단하며, 일부 사용자는 데이터 사용을 위해 이미지를 차단하도록 설정을 변경합니다. 따라서 이미지를 다운로드하지 않으면 전체 메시지가 손실될 수 있습니다. 이를 방지하려면

* 콘텐츠와 이미지 및 텍스트의 균형을 맞출 수 있습니다. 이미지 기반의 이메일 전달

* 이미지에 텍스트를 포함해야 하는 경우 대체 및 제목 텍스트를 사용하여 메시지가 제대로 전달되는지 확인하십시오. 대체/제목 텍스트에 스타일을 지정하여 모양을 향상시킬 수 있습니다.

* 일부 이메일 클라이언트에서 지원하지 않는 배경 이미지는 사용하지 마십시오.

### 반응형 이미지 제작

반응형 이미지를 만들고 크기를 조정할 수 있습니다. 이렇게 하면 구축하는 데 시간이 더 걸리기 때문에 비용 측면에서 영향을 줄 수 있습니다.

### 절대 이미지 참조 사용

외부에서 액세스하려면 캠페인에 연결된 이메일 및 공개 리소스에 사용된 이미지가 외부에서 액세스 가능한 서버에 있어야 합니다.

* 인스턴스 구성이 공개 리소스 관리를 활성화하는지 확인할 수 있습니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 배달 마법사에서 이미지가 포함된 HTML 페이지를 가져오거나 아이콘을 통해 HTML 편집기를 사용하여 직접 이미지를 삽입할 수 **[!UICONTROL Image]** 있습니다. [자세히 알아보기](../../delivery/using/defining-the-email-content.md#adding-images)

* 이미지가 표시되지 않으면 서버에서 이미지를 사용할 수 있는지 확인하십시오. 이렇게 하려면 게재에서 소스 탭을 클릭합니다. 이미지를 찾아 웹 브라우저에서 각 이미지의 URL을 복사하여 붙여넣습니다. 이미지가 표시되지 않으면 IT 관리자나 배달 내용을 제공하는 타사 공급업체에 문의하십시오.

## 메시지 미리 보기 {#preview-msg}

Adobe은 메시지를 미리 보고 개인화와 수신자가 전달을 어떻게 볼 수 있는지 확인하는 것이 좋습니다.

* 전달 창에서 **[!UICONTROL Preview]** 하위 탭을 사용하여 수신자의 각 컨텐츠 렌더링을 볼 수 있습니다. 개인화 필드 및 컨텐츠 조건부 요소는 선택한 프로필에 대한 해당 정보로 대체됩니다. [자세히 알아보기](../../delivery/using/defining-the-email-content.md#message-content)

* 각 미리 보기 중에 스팸 방지 자동 검사가 수행됩니다. 하위 **[!UICONTROL Preview]** 탭에서 SpamAsser [스팸 점수](../../delivery/using/spamassassin.md) 지정을 확인합니다.  경고 **[!UICONTROL More...]** 에 대한 자세한 내용을 보려면 을 클릭합니다.  SpamAsser가 Adobe Campaign 응용 프로그램 서버에 올바르게 설치 및 구성되어 있는지 확인하십시오. [자세히 알아보기](../../installation/using/configuring-spamassassin.md)
