---
product: campaign
title: 개인 정보 보호 요청 만들기
description: 개인 정보 보호 요청을 만들고 관리하는 방법을 알아봅니다
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
source-git-commit: a8044037e889f59d4288a0746001e84d319f6bcf
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 94%

---

# 개인 정보 요청 만들기 및 관리 {#privacy-request-ui}

![](../../assets/v7-only.svg)

이 섹션에서는 액세스 및 삭제 요청을 만드는 방법과 Adobe Campaign이 요청을 처리하는 방법에 대해 설명합니다.

## 개인 정보 보호 요청 만들기 {#create-privacy-request-ui}

**Adobe Campaign 인터페이스**&#x200B;를 통해 개인 정보 보호 요청을 만들고 진행 상황을 추적할 수 있습니다. 새로운 개인 정보 보호 요청을 만들려면 다음 지침을 따르십시오.

1. **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Privacy Requests]** 아래의 개인 정보 보호 요청 폴더에 액세스합니다.

   ![](assets/privacy-requests-folder.png)

1. 이 화면에서는 모든 현재 개인 정보 보호 요청, 상태 및 로그를 볼 수 있습니다. **[!UICONTROL New]**&#x200B;을(를) 클릭하여 개인 정보 보호 요청을 생성합니다.

   ![](assets/privacy-request-new.png)

1. **[!UICONTROL Regulation]** (GDPR, CCPA, PDPA 또는 LGPD), **[!UICONTROL Request type]** (액세스 또는 삭제)을 선택하고 **[!UICONTROL Namespace]** (을)를 선택하고 **[!UICONTROL Reconciliation value]** (을)를 입력합니다. 이메일을 네임스페이스로 사용하는 경우 데이터 주체의 이메일을 입력합니다.

   ![](assets/privacy-request-properties.png)

개인 정보 기술 워크플로우는 매일 한 번 실행되며 각각의 새로운 요청을 처리합니다.

* Delete 요청: Adobe Campaign에 저장된 수신자 데이터가 지워집니다.
* Access 요청: Adobe Campaign에 저장된 수신자의 데이터가 생성되고 요청 화면의 왼쪽에서 XML 파일로 사용할 수 있습니다.

![](assets/privacy-request-download.png)

## 테이블 목록 {#list-of-tables}

Adobe Campaign은 Delete 또는 Access 개인 정보 보호 요청을 수행할 때 수신자 테이블(고유 유형)에 대한 링크가 있는 모든 테이블의 **[!UICONTROL Reconciliation value]**&#x200B;을(를) 기준으로 모든 데이터 주체의 데이터를 검색합니다.

다음은 개인 정보 보호 요청을 수행할 때 고려할 수 있는 기본 제공 테이블 목록입니다.

* 수신자(recipient)
* 수신자 게재 로그(broadLogRcp)
* 수신자 추적 로그(trackingLogRcp)
* 보관된 이벤트 게재 로그(broadLogEventHisto)
* 수신자 목록 콘텐츠(rcpGrpRel)
* 방문자 오퍼 제안(propositionVisitor)
* 방문자(visitor)
* 구독 내역(subHisto)
* 구독(subscription)
* 수신자 오퍼 제안(propositionRcp)

수신자 테이블(고유 유형)에 대한 링크가 있는 사용자 지정 테이블를 만든 경우, 해당 테이블도 고려됩니다. 예를 들어 수신자 테이블과 연결된 트랜잭션 테이블과 트랜잭션 테이블과 연결된 트랜잭션 세부 정보가 있는 경우, 이 두 가지 모두 고려됩니다.

>[!IMPORTANT]
>
>프로필 삭제 워크플로우를 사용하여 개인 정보 일괄 처리 요청을 수행하는 경우, 다음 사항을 고려하십시오.
>* 워크플로우를 통한 프로필 삭제는 하위 테이블을 처리하지 않습니다.
>* 모든 하위 테이블에 대해 삭제를 처리해야 합니다.
>* Adobe은 개인 정보 액세스 테이블에서 삭제할 행을 추가하고 **[!UICONTROL Delete privacy requests data]** 워크플로우에서 삭제를 수행하도록 하는 ETL 워크플로우를 만들 것을 권장합니다. 성능을 위해 삭제는 하루에 200개의 프로필로 제한하는 것이 좋습니다.


## 개인 정보 보호 요청 상태 {#privacy-request-statuses}

개인정보 보호 요청에 대한 다양한 상태는 다음과 같습니다.

* **[!UICONTROL New]** / **[!UICONTROL Retry pending]**: 진행 중이며 워크플로우는 아직 요청을 처리하지 않았습니다.
* **[!UICONTROL Processing]** / **[!UICONTROL Retry in progress]**: 워크플로우가 요청을 처리하고 있습니다.
* **[!UICONTROL Delete pending]**: 워크플로우는 삭제하려는 모든 수신자 데이터를 식별했습니다.
* **[!UICONTROL Delete in progress]**: 워크플로우가 삭제를 처리하고 있습니다.
* **[!UICONTROL Delete Confirmation Pending]**(2단계 프로세스 모드에서 Delete 요청): 워크플로우에서 Access 요청을 처리했습니다. 삭제를 수행하려면 수동 확인이 요구됩니다. 버튼은 15일 동안 사용할 수 있습니다.
* **[!UICONTROL Complete]**: 요청 처리가 오류 없이 끝났습니다.
* **[!UICONTROL Error]**: 워크플로우에서 오류가 발생했습니다. 이유는 **[!UICONTROL Request status]** 열의 개인 정보 보호 요청 목록에 표시됩니다. 예를 들어 **[!UICONTROL Error data not found]**&#x200B;은(는) 데이터 주체의 **[!UICONTROL Reconciliation value]**&#x200B;와(과) 일치하는 수신자 데이터가 데이터베이스에 없음을 의미합니다.

## 2단계 프로세스 {#two-step-process}

기본적으로 **2단계 프로세스**&#x200B;가 활성화됩니다. 이 모드를 사용하여 새 Delete 요청을 만들 때 Adobe Campaign은 항상 Access 요청을 먼저 수행합니다. 따라서 삭제를 확인하기 전에 데이터를 확인할 수 있습니다.

개인 정보 보호 요청 버전 화면에서 이 모드를 변경할 수 있습니다. **[!UICONTROL Advanced settings]**&#x200B;을(를) 클릭합니다.

![](assets/privacy-request-advanced-settings.png)

2단계 모드가 활성화되면 새 Delete 요청의 상태가 **[!UICONTROL Confirm Delete Pending]**(으)로 변경됩니다. 개인 정보 보호 요청 화면에서 생성된 XML 파일을 다운로드하고 데이터를 확인합니다. 데이터 삭제를 확인하려면 **[!UICONTROL Confirm delete data]** 버튼을 클릭합니다.

![](assets/privacy-request-delete-data.png)

## JSSP URL {#jspp-url}

Access 요청을 처리할 때 Adobe Campaign은 데이터베이스에서 수신자의 데이터를 검색하여 로컬 컴퓨터에 저장된 XML 파일로 내보내는 JSSP를 생성합니다. JSSP URL은 다음과 같이 정의됩니다.

```
"$(serverUrl)+'/nms/gdpr.jssp?id='+@id"
```

여기서 @id는 개인 정보 보호 요청 ID입니다.

이 URL은 **[!UICONTROL Privacy Requests (gdprRequest)]** 스키마의 **[!UICONTROL "File location" (@urlFile)]** 필드에 저장됩니다.

이 정보는 데이터베이스에서 90일 동안 사용할 수 있습니다. 기술 워크플로우에서 요청을 정리하면 해당 정보가 데이터베이스에서 제거되고 URL이 더 이상 사용되지 않습니다. 웹 페이지에서 데이터를 다운로드하기 전에 URL이 여전히 유효한지 확인하십시오.

다음은 데이터 주체의 데이터 파일 예입니다.

![](assets/do-not-localize/privacy-access-file.png)

데이터 컨트롤러는 해당 JSSP URL을 포함하는 웹 애플리케이션을 쉽게 만들어 데이터 주체의 데이터 파일을 웹 페이지에서 사용할 수 있도록 할 수 있습니다.

![](assets/privacy-gdpr-jssp.png)

다음은 웹 애플리케이션 **[!UICONTROL Page]** 활동의 예제로 사용할 수 있는 코드 조각입니다.

![](assets/privacy-page-activity.png)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head> <meta http-equiv="Content-Language" content="en"> <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> <link rel="stylesheet" type="text/css" href="/nl/webForms/landingPage.css"/> <title>Clickthrough</title> <style type="text/css" media="all"> /* override formulary area */ .formulary { top: 200px; position: absolute; left: 0; } </style> </head> <body style="" class="">
<center>
<div id="wrap">
<div id="header"><img class="nlui-widget" alt="placeholder_header" src="/nms/img/contentModels/placeholder_header.png" unselectable="on" />
<div class="header-title center-title">DOWNLOAD GDPR DATA</div>
<div class="formulary center-formulary"><form>
<div class="button large-button"><a href=[SERVER_URL]/nms/gdpr.jssp?id=13000" data-nl-type="externalLink">CLICK TO DOWNLOAD</a></div>
</form></div>
</div>
<div id="content">
<div class="row">
<div class="info">
<div class="desc">
<div class="title">EFFICIENCY</div>
<div class="desc">Our service is guaranteed to improve your efficiency. Increase performance and use our high-technology service to implement even the most ambitious of projects.</div>
</div>
</div>
</div>
</div>
<div id="footer">
<div style="text-align: center;">
<div style="float: left;"><a href="#">Contact us</a></div>
<div style="float: right;">&copy; Copyrights</div>
<div><a href="#"><img title="facebook" class="nlui-widget" alt="facebook" src="/xtk/img/facebook.png" unselectable="on" /></a> <a href="#"><img title="Twitter" class="nlui-widget" alt="twitter" src="/xtk/img/twitter.png" unselectable="on" /></a> <a href="#"><img title="Google" class="nlui-widget" alt="google_plus" src="/xtk/img/google_plus.png" unselectable="on" /></a> <a href="#"><img title="Linkedin" class="nlui-widget" alt="Linkedin" src="/xtk/img/linkedin.png" unselectable="on" /></a></div>
</div>
</div>
</div>
</center>
</body> </html>
```

데이터 주체의 데이터 파일에 대한 액세스가 제한되어 있으므로 웹 페이지의 익명 액세스를 비활성화해야 합니다.  **[!UICONTROL Privacy Data Right]** 권한이 명명된 연산자만 페이지에 로그온하여 데이터를 다운로드할 수 있습니다.
