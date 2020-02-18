---
title: 웹 추적 태그 만들기
seo-title: 웹 추적 태그 만들기
description: 웹 추적 태그 만들기
seo-description: null
page-status-flag: never-activated
uuid: c5599bdd-e6b8-4db4-b0ca-aaee2adc1919
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 647ca037-4efb-4524-9642-11056d096aea
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 웹 추적 태그 만들기{#creating-web-tracking-tags}

추적할 사이트의 각 페이지는 Adobe Campaign 플랫폼에서 참조되어야 합니다. 이 참조는 다음 두 가지 방법으로 수행할 수 있습니다.

1. 추적할 URL의 수동 정의,
1. 추적할 URL을 신속하게 만들 수 있습니다.

## 애플리케이션에서 추적할 URL 정의 {#defining-the-urls-to-be-tracked-in-the-application}

이 방법을 사용하면 추적할 페이지를 수동으로 정의한 다음 연관된 웹 추적 태그의 예를 생성할 수 있습니다. 이 작업은 클라이언트 콘솔의 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 노드에 정의됩니다.

![](assets/d_ncs_integration_webtracking_screen.png)

페이지에 삽입할 HTML 코드를 생성하려면 다음을 수행합니다.

* 태그 레이블을 입력합니다.추적 로그에 표시됩니다.
* 소스 URL을 가리킵니다.이 필드는 정보 용도로 사용되며 추적된 페이지를 표시할 수 있습니다(선택 사항).
* 필요한 경우 유효 기간을 입력합니다.
* HTML **[!UICONTROL Generate]** 코드를 클릭합니다.

그런 다음 생성된 코드를 복사하여 추적할 페이지에 붙여 넣습니다.

## 추적할 URL을 신속하게 만들기 {#on-the-fly-creation-of-urls-to-be-tracked}

tagid **매개 변수 값에 정보를 추가하여 웹 추적 URL을 신속하게 만들 수** 있습니다.

* 추적된 페이지 유형:웹용 &#39;w&#39;, TRANSACTION의 &#39;t&#39;,
* URL을 만들어야 하는 폴더의 내부 이름입니다.

이 두 가지 정보는 &#39;|&#39; 문자를 추가하여 추적된 페이지의 식별자와 연결해야 합니다.

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>tagid 매개 변수가 URL 매개 변수로 사용될 때 **tagid** 매개 변수의 값을 인코딩해야 합니다.

**예**:트랜잭션 유형 웹 추적 URL 생성.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
