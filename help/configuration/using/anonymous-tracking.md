---
title: 익명 추적
seo-title: 익명 추적
description: 익명 추적
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 익명 추적{#anonymous-tracking}

Adobe Campaign을 사용하면 수집된 웹 추적 정보를 수신자가 익명으로 사이트를 탐색할 때 수신자에게 연결할 수 있습니다. 사용자가 웹 사이트의 태그가 지정된 페이지를 탐색하면 이 검색 정보가 수집되므로 Adobe Campaign에서 보낸 이메일을 클릭하면 해당 페이지가 식별되고 정보가 자동으로 연결됩니다.

>[!IMPORTANT]
>
>웹 사이트에서 익명 추적을 설정하면 상당한 양의 추적 로그 모음이 트리거되어 데이터베이스 작업에 영향을 줄 수 있습니다. 주의하여 구성합니다.\
>추적 로그는 추적 데이터가 제거될 때까지 데이터베이스에 저장됩니다. 배포 마법사를 사용하여 제거 빈도를 구성합니다. For more on this, refer to [this section](../../installation/using/deploying-an-instance.md#purging-data).

인스턴스에서 익명 웹 추적을 활성화하려면 다음 요소를 구성해야 합니다.

* Server **Server** . **xml** 파일 추적 서버의 **요소 중 WebVisitors** 매개 변수는 사이트를 방문하는 사용자의 알 수 없는 인터넷 브라우저에서 &#39;**trueTrue**&#39; 추적 서버를 설정하고, 영구 쿠키를 배치하려면 &#39;conf&#39;(uuuuid20 ****)을 설정해야 합니다.
* 배포 **마법사의 추적 구성** 화면에서 익명 웹 추적 모드를 선택해야 합니다.

   ![](assets/webtracking_anonymous_set.png)

* 웹 양식 및 설문 조사는 추적 서버에서 게시하고 실행해야 합니다. 배포 마법사에서 일치 옵션을 선택해야 합니다.

   ![](assets/webtracking_publication_set_for_webapps.png)

