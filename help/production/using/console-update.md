---
product: campaign
title: 콘솔 업데이트
description: 콘솔 업데이트
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용됩니다."
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 11%

---

# 콘솔 업데이트{#console-update}



다음을 선택한 경우 **[!UICONTROL Do not request console update]** 업데이트 요청을 다시 활성화하려면 다음 절차를 적용합니다.

1. 다음을 사용하여 레지스트리 데이터베이스의 편집기를 엽니다. **regedit** Windows의 명령 **[!UICONTROL Start > Execute]** 메뉴 아래의 제품에서 사용할 수 있습니다.

   ![](assets/ncs_console_update_1.png)

1. 트리에서 의 옵션을 표시합니다 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 노드.
1. 삭제 **[!UICONTROL confAdvisedUpgrade]** 레지스트리 편집기를 입력한 후 닫습니다.

   ![](assets/ncs_console_update_2.png)
