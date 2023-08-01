---
product: campaign
title: 익명 추적
description: 익명 추적을 설정하는 방법 알아보기
feature: Configuration, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 5%

---

# 익명 추적{#anonymous-tracking}

Adobe Campaign을 사용하면 수신자가 사이트를 익명으로 검색할 때 수집된 웹 추적 정보를 연결할 수 있습니다. 사용자가 웹 사이트의 태그가 지정된 페이지를 탐색할 때 이 탐색 정보가 수집되므로 Adobe Campaign에서 보낸 이메일을 클릭하면 해당 페이지가 식별되고 정보가 자동으로 연결됩니다.

>[!IMPORTANT]
>
>웹 사이트에서 익명 추적을 설정하면 상당한 양의 추적 로그 수집이 트리거되어 데이터베이스 작업에 영향을 줄 수 있습니다. 신중하게 구성하십시오.\
>추적 로그는 추적 데이터가 삭제될 때까지 데이터베이스에 저장됩니다. 배치 마법사를 사용하여 제거 빈도를 구성합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/deploying-an-instance.md#purging-data)을 참조하십시오.

인스턴스에서 익명 웹 추적을 활성화하려면 다음 요소를 구성해야 합니다.

* 다음 **trackWebVisitor** 매개 변수 **리디렉션** 의 요소 **serverConf.xml** 추적 서버의 파일을 &#39;(으)로 설정해야 합니다.**true**&#39;, 영구 쿠키(**uuid230**) 사이트를 방문하는 알 수 없는 인터넷 사용자의 브라우저입니다.
* 다음 **익명 웹 추적** 배포 마법사의 추적 구성 화면에서 모드를 선택해야 합니다.

  ![](assets/webtracking_anonymous_set.png)

* 웹 양식은 추적 서버에서 게시되고 실행되어야 합니다. 배포 마법사에서 일치하는 옵션을 선택해야 합니다.

  ![](assets/webtracking_publication_set_for_webapps.png)
