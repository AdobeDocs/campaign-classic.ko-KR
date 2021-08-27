---
product: campaign
title: 아키텍처
description: 워크플로우는 처리 로드를 공유하기 위해 여러 서버에서 시작할 수 있는 특정 모듈에 의해 처리됩니다.
audience: workflow
content-type: reference
topic-tags: -general-operation
exl-id: 46801f78-706c-4dfa-bce7-3d15f569f222
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 1%

---

# 아키텍처 {#architecture}

![](../../assets/common.svg)

워크플로우는 특정 모듈에 의해 처리됩니다. 처리 로드를 공유하기 위해 여러 서버에서 이 모듈을 시작할 수 있습니다.

![](assets/architecture.png)

* &#39;Workflow Instance Runwf&#39;(Workflow Instance Runner) 프로세스는 지정된 워크플로 인스턴스의 모든 작업을 실행합니다. 당분간 실행할 작업이 없으면 &#39;수동적&#39;이 됩니다. 즉, 데이터베이스의 상태를 저장한 다음 중지합니다.
* 워크플로우 서버(wfserver) 모듈은 현재 워크플로우 인스턴스를 모니터링합니다. 수행할 작업이 있으면 이 모듈은 해당 인스턴스를 활성화(또는 다시 활성화)하는 프로세스를 만듭니다.
