---
product: campaign
title: 콘솔 업데이트
description: 콘솔 업데이트
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 55
ht-degree: 10%

---

# 콘솔 업데이트{#console-update}



**[!UICONTROL Do not request console update]** 옵션을 선택하고 업데이트 요청을 다시 활성화하려면 다음 절차를 적용합니다.

1. Windows **[!UICONTROL Start > Execute]** 메뉴의 **regedit** 명령을 사용하여 레지스트리 데이터베이스의 편집기를 엽니다.

   ![](assets/ncs_console_update_1.png)

1. 트리에서 **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** 노드의 옵션을 표시합니다.
1. **[!UICONTROL confAdvisedUpgrade]** 항목을 삭제하고 레지스트리 편집기를 닫습니다.

   ![](assets/ncs_console_update_2.png)
