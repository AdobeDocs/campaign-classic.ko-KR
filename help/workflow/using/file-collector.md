---
title: 파일 수집 툴
seo-title: 파일 수집 툴
description: 파일 수집 툴
seo-description: null
page-status-flag: never-activated
uuid: 57ef7b2b-f257-4d76-970f-55aece719cec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 9b937d4d-55ae-4bd4-8dc6-eea42f15b69f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 파일 수집 툴{#file-collector}

파일 **수집기는** 디렉토리에 하나 이상의 파일이 도착하는 것을 모니터링하고 수신한 각 파일에 대한 전환을 활성화합니다. 각 이벤트에 대해 **[!UICONTROL filename]** 변수에는 받은 파일의 전체 이름이 포함됩니다. 수집된 파일은 보관을 위해 다른 디렉토리로 이동되며 한 번만 카운트됩니다.

기본적으로 파일 수집기는 일정에 의해 지정된 시간에 파일의 존재를 테스트하는 영구 작업입니다.

파일은 이 워크플로를 담당하는 wfserver 모듈이 실행되는 서버에 있어야 합니다. 단일 인스턴스에 여러 개의 wfserver 모듈이 배포되는 경우 이러한 파일을 사용하는 활동의 관련성 또는 워크플로우의 전체적인 관련성을 지정해야 합니다.

## 속성 {#properties}

활동의 첫 번째 탭에서는 소스 디렉토리를 선택하고 필요한 경우 수집된 파일을 필터링할 수 **[!UICONTROL File collector]** 있습니다. 다른 탭은 인바운드 [이메일](../../workflow/using/inbound-emails.md) (**[!UICONTROL Schedule]** 및 **[!UICONTROL Expiry]** 탭)에 자세히 설명되어 있습니다.

![](assets/file_collect_edit.png)

1. **파일 다운로드**

   * **[!UICONTROL Directory]**

      다운로드할 파일이 들어 있는 디렉토리입니다. 이 디렉토리는 서버에 미리 만들어야 합니다.존재하지 않으면 오류가 발생합니다.

   * **[!UICONTROL Filter]**

      이 필터와 일치하는 파일만 고려됩니다. 디렉토리에 있는 다른 파일은 무시됩니다. 필터가 비어 있으면 디렉토리의 모든 파일이 고려됩니다. 필터 예: ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      이 옵션을 활성화하면 첫 번째 파일의 수신 후에 작업이 종료됩니다. 디렉토리에 필터에 해당하는 여러 파일이 있는 경우 하나의 파일만 고려됩니다. 이 옵션을 사용하면 하나의 이벤트만 전송됩니다. 고려된 파일은 목록의 첫 번째 알파벳순입니다.

      예약되지 않은 작업의 경우 지정된 디렉토리에 필터와 일치하는 파일이 없으면 **[!UICONTROL Process file nonexistence]** 옵션이 활성화되지 않으면 오류가 발생합니다.

   * **[!UICONTROL Execution schedule]**

      탭의 매개 변수를 통해 파일 상태 확인 빈도를 **[!UICONTROL Schedule]** 결정합니다.

1. **오류 처리**

   다음 두 옵션을 사용할 수 있습니다.

   * **[!UICONTROL Process file nonexistence]**

      이 옵션은 지정된 디렉토리에서 필터와 일치하는 파일이 없을 때마다 특수 전환을 시작합니다.

      작업이 예약되지 않은 경우 이 전환은 한 번만 활성화됩니다.

   * **[!UICONTROL Processing errors]**

      이 옵션을 사용하면 특수 전환이 나타나며 오류가 발생하는 경우 활성화됩니다. 이 경우 워크플로우는 오류 상태로 변경되지 않고 실행을 계속합니다.

      파일 시스템 오류(파일을 이동할 수 없음, 디렉토리에 액세스할 수 없음 등)를 고려하여 발생한 오류입니다.

      이 옵션은 활동 구성과 관련된 오류(예: 잘못된 값)를 처리하지 않습니다.

1. **역사**

   다음 **[!UICONTROL File historization]** 단계를 참조하십시오.웹 [다운로드](../../workflow/using/web-download.md).

파일 처리 순서를 확인할 수 없습니다. 일련의 파일을 순차적으로 처리하려면 이 **[!UICONTROL Stop as soon as a file has been processed]** 옵션을 사용하여 루프를 만듭니다. 이 경우 파일은 알파벳 순서로 처리됩니다. 이 **[!UICONTROL Process file nonexistence]** 옵션을 사용하면 반복을 완료할 수 있습니다.

![](assets/file_collect_loop.png)

## 출력 매개 변수 {#output-parameters}

* 파일

전체 파일 이름. 기록 디렉토리로 이동한 후의 파일 이름입니다. 따라서 경로는 다르지만 이름이 같은 다른 파일이 디렉토리에 이미 있는 경우에도 이름이 다릅니다. 내선 번호는 유지됩니다.
