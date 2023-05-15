---
product: campaign
title: Adobe Experience Platform 세그먼트를 Campaign에 수집
description: Adobe Experience Platform 대상을 Campaign Classic에 수집하는 방법을 알아봅니다
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Adobe Experience Platform 세그먼트를 Campaign에 수집 {#destinations}



Adobe Experience Platform 대상을 Campaign에 수집하여 워크플로우에서 사용하려면 먼저 Adobe Campaign as a Adobe Experience Platform에 연결해야 합니다 **대상** 내보낼 세그먼트로 구성합니다.

대상이 구성되면 데이터가 저장소 위치로 내보내지며 Campaign Classic에서 전용 워크플로우를 빌드하여 데이터를 수집해야 합니다.

## Adobe Campaign을 대상으로 연결

Adobe Experience Platform에서 내보낸 세그먼트에 대한 저장소 위치를 선택하여 Adobe Campaign와의 연결을 구성합니다. 이 단계에서는 내보낼 세그먼트를 선택하고 포함할 추가 XDM 필드를 지정할 수도 있습니다.

자세한 내용은 [대상 설명서](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html).

대상을 구성한 후 Adobe Experience Platform에서 제공한 저장소 위치에 탭으로 구분된 .txt 또는 .csv 파일을 만듭니다. 이 작업은 예약되어 24시간에 한 번 수행됩니다.

이제 세그먼트를 Campaign에 수집하도록 Campaign Classic 워크플로우를 구성할 수 있습니다.

## Campaign Classic에서 가져오기 워크플로우 만들기

Campaign Classic이 대상으로 구성되면 Adobe Experience Platform에서 내보낸 파일을 가져오기 위한 전용 워크플로우를 빌드해야 합니다.

이를 수행하려면 다음을 추가하고 구성해야 합니다 **[!UICONTROL File transfer]** 활동. 이 활동을 구성하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/file-transfer.md).

![](assets/rtcdp-file-transfer.png)

그런 다음 필요에 따라 워크플로우를 빌드 할 수 있습니다(세그먼트 데이터를 사용하여 데이터베이스 업데이트, 세그먼트에 크로스 채널 게재 보내기 등).

예를 들어 아래 워크플로우는 매일 저장소 위치에서 파일을 다운로드한 다음 세그먼트 데이터로 Campaign 데이터베이스를 업데이트합니다.

![](assets/rtcdp-workflow.png)
