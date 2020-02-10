---
title: 콘솔 업데이트
seo-title: 콘솔 업데이트
description: 콘솔 업데이트
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 콘솔 업데이트{#console-update}

이 **[!UICONTROL Do not request console update]** 옵션을 선택하고 업데이트 요청을 다시 활성화하려면 다음 절차를 적용합니다.

1. Windows **** **[!UICONTROL Start > Execute]** 메뉴에서 regedit 명령을 사용하여 레지스트리 데이터베이스의 편집기를 엽니다.

   ![](assets/ncs_console_update_1.png)

1. 트리에서 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 노드의 옵션을 표시합니다.
1. 항목을 **[!UICONTROL confAdvisedUpgrade]** 삭제하고 레지스트리 편집기를 닫습니다.

   ![](assets/ncs_console_update_2.png)

