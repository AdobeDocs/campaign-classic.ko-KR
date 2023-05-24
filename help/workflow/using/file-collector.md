---
product: campaign
title: 파일 수집기
description: 파일 수집기 워크플로우 활동에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 파일 수집기{#file-collector}



다음 **파일 수집기** 디렉터리에서 하나 이상의 파일 도착을 모니터링하고 수신된 각 파일에 대한 전환을 활성화합니다. 각 이벤트에 대해 **[!UICONTROL filename]** 변수에는 받은 파일의 전체 이름이 포함됩니다. 수집된 파일은 보관 목적으로 다른 디렉터리로 이동하며 한 번만 카운트되도록 합니다.

기본적으로 파일 수집기는 일정에서 지정한 시간에 파일이 있는지 테스트하는 영구 작업입니다.

파일은 이 워크플로를 담당하는 wfserver 모듈이 실행되는 서버에 있어야 합니다. 여러 wfserver 모듈이 단일 인스턴스에 배포되는 경우 이러한 파일을 사용하는 활동의 선호도 또는 워크플로의 전체 선호도를 지정해야 합니다.

## 속성 {#properties}

의 첫 번째 탭 **[!UICONTROL File collector]** 활동을 사용하면 소스 디렉터리를 선택하고 필요한 경우 수집된 파일을 필터링할 수 있습니다. 다른 탭은에 자세히 설명되어 있습니다. [인바운드 이메일](inbound-emails.md) (**[!UICONTROL Schedule]** 및 **[!UICONTROL Expiry]** 탭).

![](assets/file_collect_edit.png)

1. **파일 다운로드**

   * **[!UICONTROL Directory]**

      다운로드할 파일이 포함된 디렉터리. 이 디렉터리는 서버에서 미리 만들어야 합니다. 디렉터리가 없으면 오류가 발생합니다.

   * **[!UICONTROL Filter]**

      이 필터와 일치하는 파일만 고려합니다. 디렉터리의 다른 파일은 무시됩니다. 필터가 비어 있으면 디렉터리의 모든 파일이 고려됩니다. 필터 예: **&#42;.zip**, **가져오기-&#42;.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      이 옵션을 활성화하면 첫 번째 파일을 받은 후 작업이 종료됩니다. 필터에 해당하는 여러 파일이 디렉토리에 있는 경우 하나만 고려합니다. 이 옵션은 하나의 이벤트만 전송되도록 보장합니다. 고려하는 파일은 목록의 첫 번째 알파벳순입니다.

      예약되지 않은 활동의 경우, 지정된 디렉터리에 필터와 일치하는 파일이 없고 **[!UICONTROL Process file nonexistence]** 옵션이 활성화되지 않으면 오류가 발생합니다.

   * **[!UICONTROL Execution schedule]**

      의 매개 변수를 통해 파일 존재 확인 빈도를 결정합니다. **[!UICONTROL Schedule]** 탭.

1. **오류 처리**

   다음 두 가지 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Process file nonexistence]**

      이 옵션은 지정된 디렉터리에 필터와 일치하는 파일이 없을 때마다 특수 전환을 시작합니다.

      작업이 예약되지 않은 경우 이 전환은 한 번만 활성화됩니다.

   * **[!UICONTROL Processing errors]**

      이 옵션을 사용하면 오류가 발생하면 특별 전환이 활성화되도록 표시됩니다. 이 경우 워크플로우는 오류 상태로 변경되지 않고 실행을 계속합니다

      파일 시스템 오류(파일 이동 불가, 디렉터리 액세스 불가 등)를 고려하는 오류는 다음과 같습니다.

      이 옵션은 활동 구성과 관련된 오류, 즉 잘못된 값을 처리하지 않습니다.

1. **기록**

   다음을 참조하십시오. **[!UICONTROL File historization]** 단계: [웹 다운로드](web-download.md).

파일 처리 순서를 결정할 수 없습니다. 파일 세트를 순차적으로 처리하려면 **[!UICONTROL Stop as soon as a file has been processed]** 옵션을 선택하고 루프를 만듭니다. 이 경우 파일은 알파벳순으로 처리됩니다. 다음 **[!UICONTROL Process file nonexistence]** 옵션을 사용하면 반복을 완료할 수 있습니다.

![](assets/file_collect_loop.png)

## 출력 매개 변수 {#output-parameters}

* 파일 이름: 전체 파일 이름입니다. 기록 디렉터리로 이동한 후의 파일 이름입니다. 따라서 경로는 다르지만 동일한 이름의 다른 파일이 디렉토리에 이미 있는 경우에는 이름도 다릅니다. 확장은 유지됩니다.
