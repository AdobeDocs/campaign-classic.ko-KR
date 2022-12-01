---
product: campaign
title: 개인화된 콘텐츠 작성
description: Adobe Campaign 게재에서 개인화된 콘텐츠를 구축하는 방법을 알아봅니다
feature: Email Design, Personalization
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1288'
ht-degree: 7%

---

# 개인화된 콘텐츠 작성 {#build-personalized-content}

![](../../assets/common.svg)

메시지 콘텐츠를 디자인할 때 게재를 실행하지 못하도록 할 수 있는 일반적인 문제를 방지하십시오. 대부분의 경우 가능한 오류는 [개인화](about-personalization.md), [서식](defining-the-email-content.md#message-content) 및 [이미지](defining-the-email-content.md#adding-images).

## 개인화 최적화 {#optimize-personalization}

게재를 실행하지 못하도록 하는 일반적인 문제를 방지하고 수신자의 경험을 향상시키기 위해 Adobe Campaign에서 메시지를 개인화할 수 있습니다.

Adobe Campaign 데이터베이스에 저장된 수신자의 데이터를 사용하거나 추적, 랜딩 페이지, 구독 등을 통해 수집할 수 있습니다.
개인화 기본 사항은 [이 섹션](personalization-fields.md).

일반적으로 개인화와 관련된 오류를 방지하기 위해 메시지 콘텐츠가 제대로 디자인되었는지 확인하십시오.

**팁**: 타사 공급업체에서 제공하는 외부 파일에서 오는 개인화 필드에서 외부 HTML 콘텐츠가 잘못될 수 있습니다. 이를 방지하려면 구문, 태그, 문자 사용 등을 확인합니다. 예를 들어 Adobe Campaign 개인화 태그에는 항상 다음 양식이 있습니다. &lt;%=table.field%> 자세한 내용은 [이 섹션](about-personalization.md)을 참조하십시오.

개인화 블록에서 매개 변수를 잘못 사용하면 문제가 될 수 있습니다. 예를 들어 JavaScript의 변수는 다음과 같이 사용해야 합니다.

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

개인화 블록에 대한 자세한 내용은 [이 섹션](personalization-blocks.md).

워크플로우에서 개인화 데이터를 준비하여 게재 준비 분석을 향상시킬 수 있습니다. 개인화 데이터가 FDA(Federated Data Access)를 통해 외부 테이블에서 가져오는 경우 특별히 사용해야 합니다. 이 옵션은 다음과 같습니다 [이 섹션](personalization-fields.md#optimizing-personalization)

## 최적화된 컨텐츠 작성 {#optimize-content}

이메일을 작성할 때는 아래에 일반적인 모범 사례를 기억하십시오.

* 간편한 디자인 유지

* 모바일 사용자 주의

* 완전히 이미지 기반 이메일을 사용하지 마십시오

* 전자 메일 안전 글꼴 사용

* 특수 문자 인코딩

### 제목 줄

작업 [제목 줄](defining-the-email-content.md#message-content) 공개 비율을 개선하려면

* 너무 긴 과목은 피하세요. 최대 50자를 사용할 수 있습니다

* 스팸으로 간주될 수 있는 &quot;무료&quot; 또는 &quot;오퍼&quot;와 같은 반복 단어를 사용하지 마십시오

* 대문자와 &quot;!&quot;, &quot;£&quot;, &quot; uuid&quot;, &quot;$&quot;와 같은 특수 문자를 사용하지 마십시오

### 미러 페이지

항상 미러 페이지 링크를 포함합니다. 기본 위치는 이메일의 맨 위에 있습니다. [자세히 알아보기](sending-messages.md#generating-the-mirror-page)

### 구독 취소 링크

구독 취소 링크는 필수입니다. 이 변수는 표시적이고 유효해야 하며 양식이 작동해야 합니다. 기본적으로 메시지를 분석할 때 [유형화 규칙](steps-validating-the-delivery.md#validation-process-with-typologies) 옵트아웃 링크가 포함되었는지 확인하고 누락된 경우 경고를 생성합니다.

**팁**: 인간 오류가 항상 가능하므로 보낼 때마다 옵트아웃 링크가 올바르게 작동하는지 확인하십시오. 예를 들어 증명을 보낼 때 링크가 유효한지, 양식이 온라인 상태이고, 이 수신자 필드에 더 이상 연락하지 않음 필드가 예로 변경되었는지 확인하십시오.

옵트아웃 링크를 삽입하는 방법 알아보기 [이 섹션](personalization-blocks.md#personalization-blocks-example).

### 전자 메일 크기

성능 또는 게재 가능성 문제를 방지하기 위해 이메일의 권장 최대 크기는 거의 입니다 **35KB**. 메시지 크기를 확인하려면 **[!UICONTROL Preview]** 을(를) 탭하고 테스트 프로필을 선택합니다. 메시지 크기가 생성되면 오른쪽 상단 모서리에 표시됩니다.

전자 메일을 한도에 따라 유지하려면 다음을 고려하십시오.

* 중복 또는 사용하지 않은 스타일 제거

* 일부 이메일 콘텐츠를 랜딩 페이지로 이동

* 코드 축소

최종 전송 전에 변경 사항을 테스트해야 합니다

### SMS 길이

기본적으로 SMS의 글자 수는 GSM(이동통신 글로벌 시스템) 표준을 충족합니다. GSM 인코딩을 사용하는 SMS 메시지는 SMS당 160자, 또는 여러 부분으로 나누어 전송되는 메시지의 경우 153자로 제한됩니다.

변환은 GSM 표준에서 고려하지 않는 SMS 문자를 다른 문자로 바꾸는 작업입니다. SMS 메시지의 콘텐츠에 개인화 필드를 삽입하면 GSM 인코딩에서 고려하지 않는 문자가 들어갈 수 있습니다. 해당 채널의 SMPP 채널 설정 탭에서 해당 상자를 선택하여 문자 변환을 승인할 수 있습니다 **[!UICONTROL External account]**.
추가 정보 [이 섹션](sms-set-up.md#creating-an-smpp-external-account).

**팁**:

* SMS 메시지의 모든 문자를 그대로 유지하려는 경우, 예를 들어 적절한 이름을 변경하지 마십시오. 음역을 활성화하지 마십시오.

* 그러나 GSM 표준에서 고려하지 않는 문자가 많이 포함된 SMS 메시지에는 음역을 활성화하여 메시지 전송 비용을 제한합니다.

추가 정보 [이 섹션](sms-set-up.md#about-character-transliteration).

## 서식에 대한 작업 {#formatting}

일반적인 형식 오류를 방지하려면 다음 요소를 확인하십시오.

* 수정 **날짜 형식**: Adobe Campaign은 JavaScript 템플릿 및 XSL 스타일시트에 대한 날짜 서식 지정 기능을 제공합니다. [자세히 알아보기](formatting.md#date-display)

* 사용 **인증된 문자** 전자 메일: 이메일 주소에 유효한 문자 목록이 &quot;XtkEmail_Characters&quot; 옵션에 정의되어 있습니다. Campaign 옵션에 액세스하는 방법 알아보기 [이 섹션](../../installation/using/configuring-campaign-options.md). 특수 문자를 올바르게 처리하려면 Adobe Campaign을 유니코드로 설치해야 합니다.

* 구성 **전자 메일 인증**: 전자 메일 헤더에 DKIM 서명이 포함되어 있는지 확인합니다. DKIM(Domain Keys Identified Mail) 인증을 통해 수신 이메일 서버는 메시지가 전송되었다고 주장하는 개인 또는 엔티티에 의해 실제로 전송되었는지, 메시지 컨텐츠가 원래 전송된 시간(및 DKIM &quot;signed&quot;) 및 수신한 시간 사이에 변경되었는지 여부를 확인할 수 있습니다. 이 표준은 일반적으로 보낸 사람 또는 보낸 사람 헤더의 도메인을 사용합니다. 자세한 내용은 [Adobe 게재 가능성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 반응형 이메일 디자인

응답형 디자인은 이메일이 열려 있는 장치에 대해 최적으로 렌더링되도록 합니다.

* 웹 HTML이 아닌 응답형 이메일 HTML 사용

* 미리 보기 모드를 사용하여 증명을 전송하여 가능한 한 많은 장치에서 렌더링을 테스트합니다

* Adobe Campaign Classic DCE(디지털 콘텐츠 편집기) 모듈에는 를 통해 사용할 수 있는 모바일용 반응형 디자인 형식 템플릿이 포함되어 있습니다 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. 추가 정보 [이 문서](https://theblog.adobe.com/responsive-email-design-101/)

## 이미지 관리 {#manage-images}

이미지 사용에 대해서는 아래 지침을 따르십시오.

### 이미지 차단

일부 이메일 클라이언트는 기본적으로 이미지를 차단하며, 일부 사용자는 데이터 사용을 위해 이미지를 차단하도록 설정을 변경합니다. 따라서 이미지를 다운로드하지 않으면 전체 메시지가 손실될 수 있습니다. 이를 방지하려면 다음을 수행하십시오.

* 컨텐츠와 이미지 및 텍스트의 균형을 맞춥니다. 완전히 이미지 기반 이메일을 사용하지 마십시오.

* 이미지에 텍스트를 포함해야 하는 경우 대체 및 제목 텍스트를 사용하여 메시지가 전달되는지 확인하십시오. 대체/제목 텍스트 스타일을 지정하여 모양을 개선합니다.

* 일부 이메일 클라이언트는 배경 이미지를 지원하지 않으므로 배경 이미지를 사용하지 마십시오.

### 반응형 이미지 만들기

이미지를 반응시키고 크기를 조정할 수 있도록 합니다. 이렇게 하면 빌드하는 데 시간이 오래 걸려 비용이 발생할 수 있습니다.

### 절대 이미지 참조 사용

외부에서 액세스하려면 캠페인에 연결된 이메일 및 공개 리소스에 사용된 이미지가 외부에서 액세스할 수 있는 서버에 있어야 합니다.

* 인스턴스 구성이 공개 리소스 관리를 활성화하는지 확인할 수 있습니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 게재 마법사에서 이미지가 포함된 HTML 페이지를 가져오거나 를 통해 HTML 편집기를 사용하여 직접 이미지를 삽입할 수 있습니다. **[!UICONTROL Image]** 아이콘. [자세히 알아보기](defining-the-email-content.md#adding-images)

* 이미지가 표시되지 않으면 서버에서 이미지를 사용할 수 있는지 확인하십시오. 이렇게 하려면 게재에서 소스 탭을 클릭합니다. 이미지를 찾고 웹 브라우저에서 각 이미지의 URL을 복사하여 붙여넣습니다. 이미지가 표시되지 않으면 IT 관리자 또는 게재 콘텐츠를 제공하는 타사 공급업체에 문의하십시오.

## 메시지 미리 보기 {#preview-msg}

Adobe은 메시지를 미리 보고 개인화와 수신자가 게재를 볼 수 있는 방법을 확인하는 것을 권장합니다.

* 게재 마법사에서 **[!UICONTROL Preview]** 하위 탭에서는 수신자에 대한 각 컨텐츠 렌더링을 볼 수 있습니다. 개인화 필드 및 콘텐츠의 조건부 요소는 선택한 프로필에 대한 해당 정보로 대체됩니다. [자세히 알아보기](defining-the-email-content.md#message-content)

* 각 미리 보기 중에 자동 스팸 방지 검사가 수행됩니다. 에서 **[!UICONTROL Preview]** 하위 탭에서 다음을 확인합니다. [SpamAssassin](spamassassin.md) 스팸 점수.  클릭 **[!UICONTROL More...]** 경고에 대해 자세히 알아보기 위해  SpamAssassin이 Adobe Campaign 애플리케이션 서버에 올바르게 설치 및 구성되어 있는지 확인합니다. [자세히 알아보기](../../installation/using/configuring-spamassassin.md)
