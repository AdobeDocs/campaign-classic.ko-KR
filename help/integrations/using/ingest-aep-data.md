---
product: campaign
title: Adobe Experience Platform 세그먼트를 Campaign으로 수집
description: Adobe Experience Platform 대상자를 Campaign Classic에 수집하는 방법에 대해 알아봅니다
feature: Experience Platform Integration
audience: integrations
content-type: reference
exl-id: 6db8a653-b649-402c-8814-24826edadba7
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Adobe Experience Platform 세그먼트를 Campaign으로 수집 {#destinations}



Adobe Experience Platform 대상을 Campaign으로 수집하여 워크플로우에서 사용하려면 먼저 Adobe Campaign을 Adobe Experience Platform **대상**(으)로 연결하고 내보낼 세그먼트로 구성해야 합니다.

대상이 구성되면 데이터가 저장소 위치로 내보내지므로 이를 수집하려면 Campaign Classic에서 전용 워크플로우를 빌드해야 합니다.

## Adobe Campaign을 대상으로 연결

Adobe Experience Platform에서 내보낸 세그먼트에 대한 저장소 위치를 선택하여 Adobe Campaign과의 연결을 구성합니다. 또한 이 단계를 통해 내보낼 세그먼트를 선택하고 포함할 추가 XDM 필드를 지정할 수 있습니다.

자세한 내용은 [대상 설명서](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign.html?lang=ko)를 참조하세요.

대상이 구성되면 Adobe Experience Platform은 사용자가 제공한 저장소 위치에 탭으로 구분된 .txt 또는 .csv 파일을 생성합니다. 이 작업은 24시간에 한 번 예약되고 수행됩니다.

이제 Campaign Classic 워크플로우를 구성하여 세그먼트를 Campaign에 수집할 수 있습니다.

## Campaign Classic에서 가져오기 워크플로우 만들기

Campaign Classic이 대상으로 구성되면 Adobe Experience Platform에서 내보낸 파일을 가져올 수 있는 전용 워크플로우를 빌드해야 합니다.

이 작업을 수행하려면 **[!UICONTROL File transfer]** 활동을 추가하고 구성해야 합니다. 이 활동을 구성하는 방법에 대한 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/event-activities/file-transfer.html?lang=ko){target="_blank"}를 참조하세요.

![](assets/rtcdp-file-transfer.png)

그런 다음 필요에 따라 워크플로우를 빌드할 수 있습니다(세그먼트 데이터를 사용하여 데이터베이스 업데이트, 세그먼트로 크로스 채널 게재 보내기 등)

예를 들어 아래 워크플로우는 매일 저장소 위치에서 파일을 다운로드한 다음 세그먼트 데이터로 Campaign 데이터베이스를 업데이트합니다.

![](assets/rtcdp-workflow.png)
