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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 7%

---


# 익명 추적{#anonymous-tracking}

Adobe Campaign을 사용하면 수집된 웹 추적 정보를 수신자가 사이트를 익명으로 검색할 때 연결할 수 있습니다. 사용자가 웹 사이트의 태그가 지정된 페이지를 탐색하면 이 검색 정보가 수집되므로, 사용자가 Adobe Campaign이 보낸 이메일을 한 번 클릭하면 해당 정보가 식별되고 정보가 자동으로 해당 페이지에 연결됩니다.

>[!IMPORTANT]
>
>웹 사이트에서 익명 추적을 설정하면 상당한 양의 추적 로그 컬렉션이 트리거되어 데이터베이스 작업에 영향을 줄 수 있습니다. 주의해서 구성합니다.\
>추적 로그는 추적 데이터를 삭제할 때까지 데이터베이스에 저장됩니다. 배포 마법사를 사용하여 제거 빈도를 구성합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/deploying-an-instance.md#purging-data)을 참조하십시오.

인스턴스에서 익명 웹 추적을 활성화하려면 다음 요소를 구성해야 합니다.

* 사이트를 방문하는 사용자의 알 수 없는 인터넷 브라우저에 영구 쿠키(uuid3 **00)를 배치하려면** serverTracking **파일 추적 서버** 요소의 **trackWebVisitors** 매개 변수를 &#39;true **&#39;로 설정하여 &#39;true******&#39;가 되어야 합니다.
* 배포 마법사의 추적 구성 화면에서 **익명 웹 추적** 모드를 선택해야 합니다.

   ![](assets/webtracking_anonymous_set.png)

* 웹 양식 및 설문 조사는 추적 서버에서 게시하고 실행해야 합니다. 배포 마법사에서 일치 옵션을 선택해야 합니다.

   ![](assets/webtracking_publication_set_for_webapps.png)

