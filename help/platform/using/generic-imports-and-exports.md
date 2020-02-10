---
title: 일반 가져오기 및 내보내기
seo-title: 일반 가져오기 및 내보내기
description: 일반 가져오기 및 내보내기
seo-description: null
page-status-flag: never-activated
uuid: e98753bb-1f14-4ec7-aa3b-d5e4f1ebaef7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: a21576c7-e94c-4fe1-9e31-d89116e427f6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 일반 가져오기 및 내보내기{#generic-imports-and-exports}

Adobe Campaign은 고객 또는 잠재 고객 목록(예: 타깃팅 작업 후)을 쉽게 추출하여 타겟 모집단 중 일부가 될 수 있도록 하는 데이터 내보내기 모듈을 제공합니다.

Adobe Campaign은 외부 파일의 데이터를 데이터베이스에 제공할 수 있는 가져오기 모듈도 제공합니다.

>[!NOTE]
>
>내보내기 및 가져오기는 **[!UICONTROL Import]** 및 **[!UICONTROL Export]** 활동을 통해 워크플로우를 통해 실행되는 전용 템플릿에 구성됩니다. 일정(예: 여러 정보 시스템 간의 데이터 교환 자동화)에 따라 자동으로 반복될 수 있습니다. 필요한 경우 Adobe Campaign 트리의 **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** 노드를 통해 가끔 가져오거나 내보낼 수 있습니다.

다음 작업을 수행할 수 있습니다.

* 가져오기 또는 내보내기 템플릿을 만들고 구성합니다(아래 참조).
* 가져오기 또는 내보내기 만들기:데이터 [내보내기](../../platform/using/exporting-data.md) 또는 데이터 [가져오기를](../../platform/using/importing-data.md)참조하십시오.
* 가져오기 또는 내보내기를 실행하고 실행을 모니터링합니다. 실행 [추적을](#execution-tracking)참조하십시오.

>[!CAUTION]
>
>Campaign에서 데이터를 가져오려면 워크플로우를 통해 데이터를 가져와야 합니다. 자세한 내용은 데이터 가져오기, [가져오기 우수 사례](../../workflow/using/importing-data.md)및 [템플릿 가져오기 예제](../../workflow/using/importing-data.md#best-practices-when-importing-data) [](../../workflow/using/importing-data.md#setting-up-a-recurring-import) 섹션을 참조하십시오.

## Creating a job template {#creating-a-job-template}

가져오기 및 내보내기 템플릿은 Adobe Campaign 트리의 **[!UICONTROL Resources > Templates > Job templates]** 디렉토리에 저장됩니다.

![](assets/s_ncs_user_export_wizard_template.png)

기본적으로 이 디렉토리에는 3개의 가져오기 템플릿과 1개의 내보내기 템플릿이 있습니다. 수정해서는 안 됩니다. 이러한 템플릿을 복제하여 고유한 템플릿을 만들거나 **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** 메뉴를 통해 새 템플릿을 만들 수 있습니다.

![](assets/s_ncs_user_export_wizard_template_create.png)

프로세스 템플릿을 만드는 절차는 내보내기 마법사 [및](../../platform/using/exporting-data.md#export-wizard) 가져오기 마법사에서 [제공됩니다](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>기본 템플릿이 **[!UICONTROL Import blacklist]** 이미 블랙리스트에 추가된 전자 메일 주소 목록을 가져오도록 구성되었습니다.
> 
>또한 **[!UICONTROL New text import]** 템플릿과 **[!UICONTROL New text export]** 템플릿을 사용하여 처음부터 가져오기 또는 내보내기를 구성할 수 있습니다.

## 새 가져오기/내보내기 만들기 {#creating-a-new-import-export}

템플릿이 구성되면 Adobe Campaign의 여러 컨텍스트에서 가져오기 및 내보내기 작업을 시작할 수 있습니다.

이 모든 기능이 [가져오기](../../platform/using/importing-data.md) 또는 [내보내기](../../platform/using/exporting-data.md#export-wizard) 마법사를 엽니다.

* Adobe Campaign 작업 영역의 **[!UICONTROL Profiles and targets]** 섹션에서 **[!UICONTROL Jobs]** 링크를 클릭합니다.이렇게 하면 기존 가져오기 및 내보내기 목록으로 이동합니다.

   단추를 클릭하고 수행할 작업 유형을 선택합니다. **[!UICONTROL Create]**

   ![](assets/s_ncs_user_import_from_home.png)

* 또한 작업공간의 감독 섹션에서 가져오기 및 내보내기를 실행할 수 있습니다.두 개의 전용 링크를 통해 직접 가져오거나 내보낼 수 있습니다.

   ![](assets/s_ncs_user_import_from_production.png)

* 가져오기 및 내보내기는 Adobe Campaign 탐색기에서 실행할 수도 있습니다.

   데이터를 내보내거나 가져오려면 **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** 노드를 클릭한 다음 **[!UICONTROL New]** 아이콘을 클릭하고 **[!UICONTROL Export]** 또는 **[!UICONTROL Import]**&#x200B;을 선택합니다. 그러면 해당 마법사가 열립니다.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## 실행 추적 {#execution-tracking}

이 편집기의 상단 섹션에서 실행 추적을 볼 수 있습니다. 내보내기 마법사를 닫고 가져오기/내보내기 작업 목록을 통해 작업 실행을 볼 수 있습니다.

![](assets/s_ncs_user_export_list_and_details.png)

* 이 **[!UICONTROL Log]** 탭에서는 실행에 관한 로그 메시지를 볼 수 있습니다.
* 이 **[!UICONTROL Rejects]** 탭에는 거부된 레코드가 포함되어 있습니다. 오류가 [발생하면 동작을 참조하십시오](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>가져오기/내보내기 작업 상태가 작업 상태에 [표시됩니다](../../platform/using/importing-data.md#job-statuses).

