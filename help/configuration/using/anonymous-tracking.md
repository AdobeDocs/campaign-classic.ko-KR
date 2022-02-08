---
product: campaign
title: 익명 추적
description: 익명 추적을 설정하는 방법 알아보기
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# 익명 추적{#anonymous-tracking}

![](../../assets/v7-only.svg)

Adobe Campaign을 사용하면 수집된 웹 추적 정보를 수신자가 익명으로 사이트를 검색할 때 수신자에게 연결할 수 있습니다. 사용자가 웹 사이트의 태그가 지정된 페이지를 탐색할 때 이 검색 정보가 수집되므로 Adobe Campaign에서 보낸 이메일을 클릭하면 해당 정보가 식별되고 정보가 자동으로 해당 페이지에 연결됩니다.

>[!IMPORTANT]
>
>웹 사이트에서 익명 추적을 설정하면 상당한 양의 추적 로그 수집을 트리거하여 데이터베이스 작업에 영향을 줄 수 있습니다. 주의 깊게 구성합니다.\
>추적 로그는 추적 데이터가 제거될 때까지 데이터베이스에 저장됩니다. 배포 마법사를 사용하여 제거 빈도를 구성합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/deploying-an-instance.md#purging-data)을 참조하십시오.

인스턴스에서 익명 웹 추적을 활성화하려면 다음 요소를 구성해야 합니다.

* 다음 **trackWebVisitors** 의 매개 변수 **리디렉션** 요소의 요소 **serverConf.xml** 추적 서버의 파일은 &#39;(으)로 설정해야 합니다.**true**&#39;, 영구 쿠키(**uuid230**)을 클릭하여 사이트를 방문하는 알 수 없는 인터넷 사용자의 브라우저로 전송됩니다.
* 다음 **익명 웹 추적** 배포 마법사의 추적 구성 화면에서 모드를 선택해야 합니다.

   ![](assets/webtracking_anonymous_set.png)

* 웹 양식은 추적 서버에서 게시 및 실행해야 합니다. 배포 마법사에서 일치 옵션을 선택해야 합니다.

   ![](assets/webtracking_publication_set_for_webapps.png)
