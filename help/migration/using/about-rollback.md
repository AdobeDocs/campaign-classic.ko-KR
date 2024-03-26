---
product: campaign
title: 이전 버전으로 롤백
description: 이전 버전으로 롤백하는 방법에 대해 알아봅니다
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
audience: migration
content-type: reference
topic-tags: rollback
hide: true
hidefromtoc: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 5%

---

# 이전 버전으로 롤백{#about-rollback}



마이그레이션 후 문제가 발생하면 이전 버전의 Campaign으로 롤백해야 할 수 있습니다.

롤백 절차는 Campaign의 초기 버전에 따라 다릅니다.

다음은 v7에서 v6.1을 복원하는 절차입니다.

1. 데이터베이스의 백업을 복구하고 복원합니다.
1. 복구 **Adobe Campaign v6.back** 폴더 (**nl6.back** linux에서 이름을 로 변경합니다. **Adobe Campaign v6** (**nl6** Linux에서)를 실행하고 원래 위치로 복원합니다.
1. 수신 포트를 다시 할당하여 IIS를 다시 구성하여 IIS 웹 사이트 수준에서 Adobe Campaign v6.1의 통합을 다시 설정합니다.
1. Adobe Campaign v7 서비스를 중지합니다.
1. IIS를 다시 시작합니다.
1. Adobe Campaign v6.1 서비스를 다시 시작합니다.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->