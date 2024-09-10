---
product: campaign
title: 개인화된 콘텐츠 작성
description: Adobe Campaign 게재에서 개인화된 콘텐츠를 작성하는 방법 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Email Design, Personalization
role: User
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1293'
ht-degree: 4%

---

# 개인화된 콘텐츠 작성 {#build-personalized-content}

메시지 콘텐츠를 디자인할 때 게재를 실행할 수 없는 일반적인 문제를 방지하십시오. 대부분의 경우 가능한 오류는 [개인화](about-personalization.md), [서식](defining-the-email-content.md#message-content) 및 [이미지](defining-the-email-content.md#adding-images)와 관련이 있습니다.

## 개인화 최적화 {#optimize-personalization}

Adobe Campaign을 사용하면 게재 실행을 방해할 수 있는 일반적인 문제를 방지하고 수신자의 경험을 향상시킬 수 있으므로 메시지를 개인화할 수 있습니다.

Adobe Campaign 데이터베이스에 저장되거나 추적, 랜딩 페이지, 구독 등을 통해 수집된 수신자의 데이터를 사용할 수 있습니다.
Personalization 기본 사항은 [이 섹션](personalization-fields.md)에 나와 있습니다.

일반적으로 개인화와 관련된 오류를 방지하기 위해 메시지 콘텐츠가 제대로 디자인되었는지 확인하십시오.

**팁**: 서드파티 공급업체에서 제공한 외부 파일에서 가져온 개인화 필드에서 외부 HTML 콘텐츠가 잘못될 수 있습니다. 이를 방지하려면 구문, 태그 사용, 문자 등을 확인합니다. 예를 들어 Adobe Campaign 개인화 태그는 항상 &lt;%=table.field%> 형식을 갖습니다. 자세한 내용은 [이 섹션](about-personalization.md)을 참조하십시오.

개인화 블록에서 매개 변수를 잘못 사용하면 문제가 될 수 있습니다. 예를 들어 JavaScript의 변수는 다음과 같이 사용해야 합니다.

    &lt;%
    
    var 브랜드 = &quot;xxx&quot;
    
    %>

개인화 블록에 대한 자세한 내용은 [이 섹션](personalization-blocks.md)을 참조하세요.

워크플로우에서 개인화 데이터를 준비하여 게재 준비 분석을 개선할 수 있습니다. 개인화 데이터가 FDA(Federated Data Access)를 통해 외부 테이블에서 제공되는 경우 특별히 사용해야 합니다. 이 옵션은 이 [이 섹션](personalization-fields.md#optimizing-personalization)에 설명되어 있습니다.

## 최적화된 컨텐츠 작성 {#optimize-content}

이메일을 작성할 때 아래의 일반적인 모범 사례를 염두에 두십시오.

* 디자인 간소화

* 모바일 사용자를 염두에 두십시오

* 전체 이미지 기반 이메일 방지

* 전자 메일 전용 글꼴 사용

* 특수 문자 인코딩

### 제목 줄

열람률을 향상시키려면 [제목 줄](defining-the-email-content.md#message-content)을 사용하세요.

* 너무 긴 과목은 피하세요. 최대 50자 사용

* 스팸으로 간주될 수 있는 &quot;무료&quot; 또는 &quot;오퍼&quot;와 같은 단어를 반복적으로 사용하지 마십시오

* 대문자와 &quot;!&quot;, &quot;!&quot;, &quot; €&quot;, &quot;$&quot;와 같은 특수 문자는 사용하지 마십시오.

### 페이지 미러링

항상 미러 페이지 링크를 포함하십시오. 기본 위치는 이메일의 상단입니다. [자세히 알아보기](sending-messages.md#generating-the-mirror-page)

### 구독 취소 링크

구독 취소 링크는 필수입니다. 표시 및 유효해야 하며 양식이 제대로 작동해야 합니다. 기본적으로 메시지를 분석할 때 [유형화 규칙](steps-validating-the-delivery.md#validation-process-with-typologies)이(가) 옵트아웃 링크가 포함되어 있는지 확인하고 누락된 경우 경고를 생성합니다.

**팁**: 사람의 실수는 항상 가능하므로 보낼 때마다 옵트아웃 링크가 올바르게 작동하는지 확인하세요. 예를 들어 증명을 보낼 때 링크가 유효한지, 양식이 온라인 상태인지, 이 받는 사람에게 더 이상 연락하지 않음 필드가 예로 변경되었는지 확인합니다.

이 섹션](personalization-blocks.md#personalization-blocks-example)에서 옵트아웃 링크 [을(를) 삽입하는 방법을 알아봅니다.

### 이메일 크기

성능 또는 게재 가능성 문제를 방지하기 위해 이메일의 권장 최대 크기는 약 **35KB**&#x200B;입니다. 메시지 크기를 확인하려면 **[!UICONTROL Preview]** 탭으로 이동하여 테스트 프로필을 선택하십시오. 생성되면 메시지 크기가 오른쪽 상단 모서리에 표시됩니다.

이메일을 제한 이하로 유지하려면 다음 사항을 고려하십시오.

* 중복 또는 사용하지 않는 스타일 제거

* 이메일 콘텐츠 일부를 랜딩 페이지로 이동

* 코드 축소

최종 전송 전에 모든 변경 사항을 테스트해야 합니다

### SMS 길이

기본적으로 SMS의 문자 수는 GSM(이동통신 글로벌 시스템) 표준을 충족합니다. GSM 인코딩을 사용하는 SMS 메시지는 SMS당 160자, 또는 여러 부분으로 나누어 전송되는 메시지의 경우 153자로 제한됩니다.

변환은 GSM 표준에서 고려하지 않는 SMS 문자를 다른 문자로 바꾸는 작업입니다. SMS 메시지의 콘텐츠에 개인화 필드를 삽입하면 GSM 인코딩에서 고려하지 않는 문자가 들어갈 수 있습니다. 해당 **[!UICONTROL External account]**의 SMPP 채널 설정 탭에서 해당 상자를 선택하여 문자 변환을 승인할 수 있습니다.
자세한 내용은 [이 섹션](sms-set-up.md#creating-an-smpp-external-account)을 참조하세요.

**팁**:

* SMS 메시지의 모든 문자를 그대로 유지하려면 적절한 이름을 변경하지 마십시오(예: 음역을 활성화하지 마십시오).

* 그러나 SMS 메시지에 GSM 표준에서 고려하지 않는 문자가 많이 포함된 경우 음역을 활성화하여 메시지 전송 비용을 제한하십시오.

자세한 내용은 [이 섹션](sms-set-up.md#about-character-transliteration)을 참조하세요.

## 서식 지정 작업 {#formatting}

일반적인 서식 오류를 방지하려면 다음 요소를 확인하십시오.

* **날짜 서식** 수정: Adobe Campaign에서는 JavaScript 서식 파일 및 XSL 스타일시트에 날짜 서식 함수를 제공합니다. [자세히 알아보기](formatting.md#date-display)

* 이메일의 **승인된 문자** 사용: 이메일 주소에 대한 유효한 문자 목록이 &quot;XtkEmail_Characters&quot; 옵션에 정의되어 있습니다. 이 섹션](../../installation/using/configuring-campaign-options.md)에서 Campaign 옵션 [에 액세스하는 방법을 알아봅니다. 특수 문자를 올바르게 처리하려면 Adobe Campaign이 유니코드에 설치되어 있어야 합니다.

* **전자 메일 인증** 구성: 전자 메일 헤더에 DKIM 서명이 포함되어 있는지 확인하십시오. DKIM(Domain Keys Identified Mail) 인증을 사용하면 수신 이메일 서버에서 메시지가 전송되었다고 주장하는 사람이나 엔티티가 실제로 메시지를 보냈는지 확인하고, 원래 보낸 시간(및 DKIM &quot;서명됨&quot;)과 받은 시간 사이에 메시지 콘텐츠가 변경되었는지 여부를 확인할 수 있습니다. 이 표준은 일반적으로 보낸 사람 또는 보낸 사람 헤더의 도메인을 사용합니다. 자세한 내용은 [Adobe 전달성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)를 참조하세요.

### 반응형 이메일 디자인

반응형 디자인은 이메일이 열린 장치에 맞게 최적으로 렌더링되도록 합니다.

* 웹 HTML 대신 반응형 이메일 HTML 사용

* 미리 보기 모드를 사용하고 증명을 전송하여 최대한 많은 장치에서 렌더링을 테스트합니다.

* Adobe Campaign Classic DCE(디지털 콘텐츠 편집기) 모듈에는 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**&#x200B;을(를) 통해 사용할 수 있는 모바일용 반응형 디자인 서식 템플릿이 포함되어 있습니다. 이 문서에서 [자세히 알아보기](https://theblog.adobe.com/responsive-email-design-101/)

## 이미지 관리 {#manage-images}

이미지 사용과 관련하여 아래 지침을 따르십시오.

### 이미지 차단 방지

일부 이메일 클라이언트는 기본적으로 이미지를 차단하며, 일부 사용자는 설정을 변경하여 데이터 사용 시 저장할 이미지를 차단합니다. 따라서 이미지를 다운로드하지 않으면 전체 메시지가 손실될 수 있습니다. 이 문제를 방지하려면

* 이미지 및 텍스트와 콘텐츠의 균형을 맞추십시오. 전체 이미지 기반 이메일을 사용하지 마십시오.

* 이미지에 텍스트가 포함되어야 하는 경우에는 대체 및 제목 텍스트를 사용하여 메시지가 전달되는지 확인하십시오. 대체/제목 텍스트의 스타일을 지정하여 모양을 개선합니다.

* 일부 이메일 클라이언트에서는 배경 이미지를 지원하지 않으므로 배경 이미지를 사용하지 마십시오.

### 이미지 반응형 만들기

반응형 및 크기 변경이 가능한 이미지를 만드십시오. 빌드하는 데 시간이 더 오래 걸리기 때문에 비용에 영향을 줄 수 있습니다.

### 절대 이미지 참조 사용

외부에서 액세스할 수 있으려면 캠페인에 연결된 이메일 및 공개 리소스에 사용된 이미지가 외부에서 액세스할 수 있는 서버에 있어야 합니다.

* 인스턴스 구성이 공개 리소스 관리를 활성화하는지 확인할 수 있습니다. [자세히 알아보기](../../installation/using/deploying-an-instance.md#managing-public-resources)

* 게재 도우미에서 이미지가 포함된 HTML 페이지를 가져오거나 **[!UICONTROL Image]** 아이콘을 통해 HTML 편집기를 사용하여 직접 이미지를 삽입할 수 있습니다. [자세히 알아보기](defining-the-email-content.md#adding-images)

* 이미지가 표시되지 않으면 서버에서 사용할 수 있는지 확인하십시오. 이렇게 하려면 게재에서 Source 탭을 클릭합니다. 이미지를 찾아 웹 브라우저에서 각 이미지의 URL을 복사하여 붙여넣습니다. 이미지가 표시되지 않으면 IT 관리자 또는 게재 콘텐츠를 제공하는 서드파티 공급업체에 문의하십시오.

## 메시지 미리 보기 {#preview-msg}

Adobe은 메시지를 미리 보고 개인화와 수신자가 게재를 보는 방법을 확인할 것을 권장합니다.

* 게재 도우미에서 **[!UICONTROL Preview]** 하위 탭을 사용하면 수신자에 대한 각 콘텐츠의 렌더링을 볼 수 있습니다. 개인화 필드 및 컨텐츠의 조건부 요소는 선택한 프로필에 대한 해당 정보로 대체됩니다. [자세히 알아보기](defining-the-email-content.md#message-content)

* 각 미리 보기 중에 자동 스팸 방지 검사가 수행됩니다. **[!UICONTROL Preview]** 하위 탭에서 [SpamAssassin](spamassassin.md) 스팸 점수를 확인하십시오.  경고에 대한 자세한 내용을 보려면 **[!UICONTROL More...]**&#x200B;을(를) 클릭하십시오.  이렇게 하려면 먼저 Adobe Campaign 애플리케이션 서버에 SpamAssassin이 올바르게 설치 및 구성되어 있는지 확인하십시오. [자세히 알아보기](../../installation/using/configuring-spamassassin.md)
