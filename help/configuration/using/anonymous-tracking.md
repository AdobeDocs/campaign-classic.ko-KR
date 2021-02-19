---
solution: Campaign Classic
product: campaign
title: 익명 추적
description: 익명 추적
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---


# 익명 추적{#anonymous-tracking}

Adobe Campaign을 사용하면 수집된 웹 추적 정보를 수신자가 사이트를 익명으로 검색할 때 연결할 수 있습니다. 사용자가 웹 사이트의 태그가 지정된 페이지를 탐색하면 이 검색 정보가 수집되므로 Adobe Campaign에서 보낸 이메일을 클릭하면 해당 정보가 식별되고 정보가 자동으로 해당 페이지에 연결됩니다.

>[!IMPORTANT]
>
>웹 사이트에서 익명 추적을 설정하면 상당한 양의 추적 로그 모음이 트리거되어 데이터베이스 작업에 영향을 줄 수 있습니다. 신중하게 구성합니다.\
>추적 로그는 추적 데이터를 삭제할 때까지 데이터베이스에 저장됩니다. 배포 마법사를 사용하여 제거 빈도를 구성합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/deploying-an-instance.md#purging-data)을 참조하십시오.

인스턴스에서 익명 웹 추적을 활성화하려면 다음 요소를 구성해야 합니다.

* 추적 서버의 **serverConf.xml** 파일의 **redirection** 요소의 **trackWebVisitors** 매개 변수를 &#39;**true**&#39;(영구 쿠키(**uuid230**))로 설정해야 합니다. 을 참조하십시오.
* 배포 마법사의 추적 구성 화면에서 **익명 웹 추적** 모드를 선택해야 합니다.

   ![](assets/webtracking_anonymous_set.png)

* 웹 양식 및 설문 조사는 추적 서버에 게시하고 실행해야 합니다. 배포 마법사에서 일치 옵션을 선택해야 합니다.

   ![](assets/webtracking_publication_set_for_webapps.png)

