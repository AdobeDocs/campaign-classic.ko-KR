---
title: v6.02의 특정 구성
seo-title: v6.02의 특정 구성
description: v6.02의 특정 구성
seo-description: null
page-status-flag: never-activated
uuid: ea072af3-fdc1-4828-ad13-d4327de1eaf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: 87a6cbda-54a6-4dae-8224-e06dc217f4fc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# v6.02의 특정 구성{#specific-configurations-in-v6-02}

다음 섹션에서는 v6.02에서 마이그레이션할 때 필요한 추가 구성에 대해 자세히 설명합니다.일반 구성 [](../../migration/using/general-configurations.md) 섹션에 설명된 설정을 구성해야 합니다.

## 웹 애플리케이션 {#web-applications}

v6.02에서 마이그레이션하는 경우 개요 유형 웹 응용 프로그램에 대한 오류 로그가 나타날 수 있습니다. 오류 메시지 예:

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

이러한 웹 응용 프로그램은 SQLData를 사용하며 보안이 강화되어 v7과 호환되지 않습니다. 이러한 오류로 인해 마이그레이션 오류가 발생합니다.

이러한 웹 애플리케이션을 사용하지 않은 경우 다음 정리 스크립트를 실행하고 업그레이드 후 를 다시 실행하십시오.

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

이러한 웹 애플리케이션을 수정했으며 v7에서 계속 사용하려면 다른 보안 영역에서 **allowSQLInjection** 옵션을 활성화하고 업그레이드 후 다시 시작해야 합니다. 자세한 내용은 [SQLData](../../migration/using/general-configurations.md#sqldata) 섹션을 참조하십시오.

## 사용자 친화성:홈 페이지 및 탐색 {#user-friendliness--home-page-and-navigation}

>[!CAUTION]
>
>v6.02 개요 형식의 웹 응용 프로그램을 계속 사용하려면 업그레이드 후 업그레이드 전에 다른 보안 영역에서 **allowSQLInjection** 옵션을 활성화해야 합니다. 웹 [애플리케이션을](#web-applications)참조하십시오.

버전 6.02에서 마이그레이션한 후 Adobe Campaign v6.02 홈 페이지가 더 이상 표시되지 않지만 여전히 액세스할 수 있으며 Adobe Campaign v7과 호환됩니다.

v6.02 홈 페이지를 계속 사용하려면 마이그레이션 후 &quot;호환성&quot; 패키지를 설치해야 합니다.

이렇게 하려면 호환성 패키지를 가져옵니다.

을 **[!UICONTROL Tools > Advanced > Import package]** 클릭하고 **에서 campaignMigration.xml** 패키지를 **`\nl\datakit\nms\[Your language]\package\optional`**&#x200B;선택합니다.

v6.02 웹 응용 프로그램 유형 인터페이스에 액세스할 수 있도록 하려면 **serverConf** .xml **파일에서 sessionTokenOnly** 서버 구성 옵션을 활성화해야 합니다.

```
sessionTokenOnly="true"
```

이 옵션은 인터페이스 호환성을 보장하기 위해 보안 수준을 변경합니다.

패키지가 설치되면 Adobe Campaign v7 홈 페이지가 v7의 일반 구성(파란색 홈 페이지 배너)이 포함된 이전 v6.02 홈 페이지로 바뀝니다.

![](assets/dashboards.png)

목록(**[!UICONTROL operation list]**, **[!UICONTROL delivery tracking in operations]**&#x200B;등)을 제외한 이 홈 페이지의 모든 링크는 v7 화면에 연결됩니다. v6.02 개요에 대한 링크(웹 애플리케이션)입니다.

![](assets/dashboards2.png)

v6.02에 구성된 다른 개요를 추가하려면 대시보드에서 홈 페이지에 추가해야 합니다.(**[!UICONTROL Administration > Access management > Dashboard]** 2).

>[!NOTE]
>
>연결을 해제한 다음 콘솔을 다시 연결하여 수정 사항을 등록하십시오.

## 메시지 센터 {#message-center}

메시지 센터에서 인스턴스 마이그레이션을 제어한 후 트랜잭션 메시지 템플릿을 다시 게시하여 제대로 작동하는지 확인해야 합니다.

v7에서 실행 인스턴스에 대한 트랜잭션 메시지 템플릿의 이름이 변경되었습니다. 현재 이 변수에는 만들어진 컨트롤 인스턴스에 해당하는 연산자 이름 앞에 **컨트롤1_template1_rt** (여기서 **control1은** 연산자의 이름)가 붙습니다. 대량의 템플릿이 있는 경우 제어 인스턴스에서 이전 템플릿을 삭제하는 것이 좋습니다.
