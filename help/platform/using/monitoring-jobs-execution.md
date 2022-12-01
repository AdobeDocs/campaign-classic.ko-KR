---
product: campaign
title: 작업 실행 모니터링
description: 가져오기 및 내보내기 작업 실행을 모니터링하는 방법을 알아봅니다.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 415c5137-2eb0-4581-a46e-26e8e3d264fa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 11%

---

# 작업 실행 모니터링 {#monitoring-job-execution}

![](../../assets/common.svg)

가져오기/내보내기 작업 목록에서 직접 가져오기 및 내보내기 작업의 실행을 추적할 수 있습니다.

![](assets/s_ncs_user_export_list_and_details.png)

* 다음 **[!UICONTROL Journal]** 탭에서는 실행에 관련된 로그 메시지를 볼 수 있습니다.
* 다음 **[!UICONTROL Rejects]** 탭에는 거부된 레코드가 포함되어 있습니다. [이 섹션](../../platform/using/executing-import-jobs.md#behavior-in-the-event-of-an-error)을 참조하십시오.

에서 **[!UICONTROL General]** 탭, **[!UICONTROL Status]** 필드는 작업의 현재 상태를 나타냅니다.

각 상태는 특수 아이콘 및 레이블로 표시됩니다. 상태 및 아이콘은 다음과 같습니다.

![](assets/s_ncs_user_export_status.png)

* **편집 진행 중**

   작업을 만들고 있습니다.

* **실행 진행 중**

   작업이 실행 중입니다.

* **취소**

   을(를) 클릭합니다. **[!UICONTROL Cancel]** 버튼: 진행 중인 작업이 취소되었습니다.

* **취소 진행 중**

   취소 명령이 고려되었으며 작업이 취소되었습니다.

* **일시 중단 진행 중**

   클릭 **[!UICONTROL Pause]**: 작업이 일시 중단되었습니다.

* **일시 중단됨**

   클릭 **[!UICONTROL Pause]**: 작업이 일시 중단되었습니다. 를 클릭하여 다시 시작할 수 있습니다 **[!UICONTROL Start]**.

* **완료됨**

   작업 실행이 완료되었습니다.

* **오류로 완료**

   기술 오류로 인해 작업이 실행되지 않았습니다.

* **서버 종료 진행 중**

   Adobe Campaign 서버가 종료되었기 때문에 진행 중인 작업이 중단되었습니다.
