---
product: campaign
title: 웹 다운로드
description: 웹 다운로드 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 1%

---

# 웹 다운로드{#web-download}



다음 **웹 다운로드** 활동은 명시적 URL, 외부 계정 또는 Adobe Campaign 인스턴스에서 파일 다운로드를 시작합니다. HTTP 프로토콜이 사용됩니다. GET 또는 POST 다운로드일 수 있습니다.

## 속성 {#properties}

1. **웹 파일 선택**

   다운로드할 파일을 지정하려면 파일 URL을 입력하거나, 파일이 저장된 외부 HTTP 계정을 사용하거나, Adobe Campaign 인스턴스를 통해 파일을 로드할 수 있습니다. 사용 가능한 매개 변수는 아래에 자세히 설명되어 있습니다.

   * 다운로드할 파일의 URL을 직접 입력하려면 **[!UICONTROL Explicit URL]** 옵션을 선택하고 적절한 필드에 URL을 지정합니다. 이 URL은 변수 데이터로 구성할 수 있습니다.

      ![](assets/download_web_edit.png)

   * 을(를) 사용하려면 **[!UICONTROL External account]**&#x200B;을 클릭하고 드롭다운 목록에서 계정을 선택한 다음 다운로드할 파일을 지정합니다.

      외부 계정은 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign 트리의 노드입니다. 계정 매개 변수는 **[!UICONTROL Edit link]** 아이콘.

      ![](assets/download_web_edit_external.png)

   * Adobe Campaign 인스턴스에서 파일을 다운로드하려면 **[!UICONTROL Adobe Campaign Instance]** 옵션을 선택합니다.

      ![](assets/download_web_edit_instance.png)

1. **파일 기록**

   다음 **[!UICONTROL File historization settings...]** 링크를 사용하여 파일 저장 디렉토리와 이 디렉토리의 비우기 빈도를 지정할 수 있습니다.

   ![](assets/download_web_edit_hist.png)

   다음 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Use a default storage directory]**: 파일이 항상 처리 전에 이동됩니다. 이 옵션을 선택하면 파일이 기본 저장소 디렉터리( **변수** Adobe Campaign 설치 폴더의 디렉터리입니다. 스토리지 디렉토리를 지정하려면 이 상자의 선택을 취소하고 **[!UICONTROL Storage directory]** 필드
   * **[!UICONTROL Number of files]**: 스토리지 디렉터리에 보관할 최대 파일 수를 입력합니다.
   * **[!UICONTROL Maximum size (in Mb)]**: 스토리지 디렉토리의 최대 용량(mb)을 입력합니다.

   각 파일은 정의된 삭제 규칙을 적용하기 전에 24시간 동안 보관됩니다. 제거는 활동 시작 바로 전에 수행되므로 진행 중인 워크플로우 파일은 고려하지 않습니다.

   파일은 해당 기간(가장 오래된 파일부터 가장 최근 파일까지)에 따라 삭제됩니다. 두 제거 규칙이 모두 확인될 때까지 가장 오래된 파일이 제거됩니다. 따라서 100개 파일 제한이 정의된 경우 스토리지 디렉토리에는 항상 워크플로가 시작되기 전에 100개의 최신 파일과 진행 중인 워크플로에서 처리 중인 파일이 포함됩니다.

   에 대한 제한을 더 이상 설정하지 않으려는 경우 **[!UICONTROL Number of files]** 및 **[!UICONTROL Maximum size (in Mb)]** 옵션에서 값으로 0을 입력합니다.

1. **고급 매개 변수**

   다음 **[!UICONTROL Advanced parameters...]** 링크를 사용하면 아래에 표시된 추가 옵션을 지정할 수 있습니다.

   ![](assets/download_web_edit_advanced.png)

   다음 **[!UICONTROL Process errors]** 옵션이에 자세히 설명되어 있습니다. [처리 오류](monitoring-workflow-execution.md#processing-errors).

## 출력 매개 변수 {#output-parameters}

* filename: 다운로드한 파일의 전체 이름입니다.
