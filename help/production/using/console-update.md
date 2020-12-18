---
solution: Campaign Classic
product: campaign
title: 콘솔 업데이트
description: 콘솔 업데이트
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# 콘솔 업데이트{#console-update}

**[!UICONTROL Do not request console update]** 옵션을 선택하고 업데이트 요청을 다시 활성화하려면 다음 절차를 적용합니다.

1. Windows **[!UICONTROL Start > Execute]** 메뉴에서 **regedit** 명령을 사용하여 레지스트리 데이터베이스의 편집기를 엽니다.

   ![](assets/ncs_console_update_1.png)

1. 트리에서 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 노드의 옵션을 표시합니다.
1. **[!UICONTROL confAdvisedUpgrade]** 항목을 삭제하고 레지스트리 편집기를 닫습니다.

   ![](assets/ncs_console_update_2.png)

