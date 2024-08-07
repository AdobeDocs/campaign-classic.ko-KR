---
product: campaign
title: 웹 추적 태그 만들기
description: 웹 추적 태그를 만드는 방법 알아보기
feature: Application Settings
role: Data Engineer, Developer
exl-id: 160df6e1-43e5-4eb9-ad2f-5db444e314ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# 웹 추적 태그 만들기{#creating-web-tracking-tags}

추적하려는 사이트의 각 페이지는 Adobe Campaign 플랫폼에서 참조되어야 합니다. 이 참조는 다음 두 가지 방법으로 수행할 수 있습니다.

1. 추적할 URL의 수동 정의,
1. 추적할 URL의 즉시 만들기.

## 애플리케이션에서 추적할 URL 정의 {#defining-the-urls-to-be-tracked-in-the-application}

이 방법을 사용하면 추적할 페이지를 수동으로 정의한 다음 연관된 웹 추적 태그의 예를 생성할 수 있습니다. 이 작업은 클라이언트 콘솔의 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 노드에 정의되어 있습니다.

![](assets/d_ncs_integration_webtracking_screen.png)

페이지에 삽입할 HTML 코드를 생성하려면:

* 태그의 레이블을 입력합니다. 이 레이블은 추적 로그에 표시됩니다.
* 소스 URL 표시: 이 필드는 정보용이며 추적된 페이지를 표시할 수 있습니다(선택 사항).
* 필요한 경우 유효 기간을 입력하고
* **[!UICONTROL Generate]** HTML 코드를 클릭합니다.

그런 다음 생성된 코드를 복사하여 추적할 페이지에 붙여넣습니다.

## 추적할 URL의 즉시 생성 {#on-the-fly-creation-of-urls-to-be-tracked}

**tagid** 매개 변수 값에 정보를 추가하여 웹 추적 URL을 바로 만들 수 있습니다.

* 추적된 페이지 유형: WEB의 경우 &#39;w&#39;, TRANSACTION의 경우 &#39;t&#39;,
* URL을 만들어야 하는 폴더의 내부 이름입니다.

이 두 정보는 &#39;|&#39; 문자를 추가하여 추적된 페이지의 식별자와 연결해야 합니다.

```
tagid=<identifier>|<type>|<foldername>
```

>[!IMPORTANT]
>
>**tagid** 매개 변수의 값을 URL 매개 변수로 사용할 때는 인코딩해야 합니다.

**예**: 트랜잭션 유형 웹 추적 URL을 만듭니다.

**http://myserver.adobe.com/r/a?tagid=home%7Ct%7CMyFolder**
