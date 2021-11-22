---
product: campaign
title: 콘솔 업데이트
description: 콘솔 업데이트
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# 콘솔 업데이트{#console-update}

![](../../assets/v7-only.svg)

을(를) 선택한 경우 **[!UICONTROL Do not request console update]** 옵션을 선택하고 업데이트 요청을 다시 활성화하려면 다음 절차를 적용합니다.

1. 를 사용하여 레지스트리 데이터베이스의 편집기를 엽니다. **regedit** Windows의 명령 **[!UICONTROL Start > Execute]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![](assets/ncs_console_update_1.png)

1. 트리에서 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 노드 아래에 있어야 합니다.
1. 삭제 **[!UICONTROL confAdvisedUpgrade]** 레지스트리 편집기를 입력하고 닫습니다.

   ![](assets/ncs_console_update_2.png)
