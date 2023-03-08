---
product: campaign
title: Campaign에서 Adobe Experience Platform으로 데이터 내보내기
description: Campaign Classic에서 Adobe Experience Platform으로 데이터를 내보내는 방법을 알아봅니다.
audience: integrations
content-type: reference
exl-id: 8d1404c5-030b-47fe-a4c3-e72f15f09bbb
source-git-commit: 89a18ae9ec57376d6ebec6c416c7562f960eb882
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 4%

---

# Campaign에서 Adobe Experience Platform으로 데이터 내보내기 {#sources}

![](../../assets/v7-only.svg)

Campaign Classic 데이터를 RTCDP(Adobe Real-time Customer Data Platform)로 내보내려면 먼저 Campaign Classic에서 공유할 데이터를 S3 또는 Azure Blob 저장소 위치로 내보내는 워크플로우를 빌드해야 합니다.

워크플로우가 구성되고 데이터가 저장소 위치로 전송되면 S3 또는 Azure Blob 저장소 위치를 로 연결해야 합니다. **소스** Adobe experience Platform에서.

>[!NOTE]
>
>Campaign 생성 데이터만 내보내는 것이 좋습니다(예: 전송, 열기, 클릭 등). Adobe Experience Platform으로. CRM과 같은 타사 소스에서 수집된 데이터는 Adobe Experience Platform으로 직접 가져와야 합니다.

## Campaign Classic에서 내보내기 워크플로우 만들기

Campaign Classic에서 S3 또는 Azure Blob 저장소 위치로 데이터를 내보내려면 내보낼 데이터를 타겟팅하는 워크플로우를 빌드하여 저장소 위치로 보내야 합니다.

이렇게 하려면 다음을 추가하고 구성합니다.

* An **[!UICONTROL Data extraction (file)]** 활동을 통해 타깃팅된 데이터를 CSV 파일로 추출할 수 있습니다. 이 활동을 구성하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/extraction--file-.md).

   ![](assets/rtcdp-extract-file.png)

* A **[!UICONTROL File transfer]** 활동을 통해 CSV 파일을 저장소 위치로 전송합니다. 이 활동을 구성하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/file-transfer.md).

   ![](assets/rtcdp-file-transfer.png)

예를 들어 아래 워크플로우는 정기적으로 로그를 CSV 파일로 추출한 다음 파일을 저장소 위치로 전송합니다.

![](assets/aep-export.png)

## 저장소 위치를 소스로 연결

S3 또는 Azure Blob 저장소 위치를 로 연결하는 주요 단계 **소스** Adobe experience Platform의 은 아래에 나열되어 있습니다. 이러한 각 단계에 대한 자세한 내용은 [소스 커넥터 설명서](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=ko).

1. Adobe Experience Platform에서 **[!UICONTROL Sources]** 메뉴에서 스토리지 위치에 대한 연결을 만듭니다.

   * [Amazon S3 소스 연결 만들기](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Azure Blob 커넥터](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >저장소 위치는 Amazon S3, 암호가 있는 SFTP, SSH 키가 있는 SFTP 또는 Azure Blob 연결일 수 있습니다. Adobe Campaign에 데이터를 보내는 기본 방법은 Amazon S3 또는 Azure Blob를 사용하는 것입니다.

   ![](assets/rtcdp-connector.png)

1. 클라우드 스토리지 배치 연결에 대한 데이터 흐름을 구성합니다. 데이터 흐름은 저장소 위치에서 Adobe Experience Platform 데이터 세트로 데이터를 검색하고 수집하는 예약된 작업입니다. 이 단계에서는 데이터 선택 및 CSV 필드를 XDM 스키마에 매핑하는 것을 포함하여 스토리지 위치에서 데이터 수집을 구성할 수 있습니다.

   자세한 정보는 다음 위치에서 확인할 수 있습니다. [이 페이지](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html).

   ![](assets/rtcdp-map-xdm.png)

1. 소스가 구성되면 Adobe Experience Platform은 사용자가 제공한 저장소 위치에서 파일을 가져옵니다.

   이 작업은 필요에 따라 예약할 수 있습니다. 인스턴스에 이미 있는 로드에 따라 하루에 최대 6번 내보내기를 수행하는 것이 좋습니다.
