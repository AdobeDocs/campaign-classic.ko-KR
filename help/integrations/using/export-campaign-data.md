---
solution: Campaign Classic
product: campaign
title: Campaign에서 Adobe Experience Platform으로 데이터 내보내기
description: Campaign Classic에서 Adobe Experience Platform으로 데이터를 내보내는 방법을 알아봅니다.
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: 1c07c3b10a6d38ca67c20746a51301d71aec0015
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---


# Campaign에서 Adobe Experience Platform {#sources}으로 데이터 내보내기

Campaign Classic 데이터를 Adobe 실시간 고객 데이터 플랫폼(RTCDP)으로 내보내려면 우선 Campaign Classic에서 워크플로우를 구축하여 공유할 데이터를 S3 또는 Azure Blob 저장소 위치로 내보내야 합니다.

워크플로우가 구성되고 데이터가 저장소 위치로 전송되면 Adobe 경험 플랫폼의 **소스**&#x200B;로 S3 또는 Azure blob 저장소 위치를 연결해야 합니다.

>[!NOTE]
>
>캠페인 생성 데이터만 내보내는 것이 좋습니다(예: 전송, 열기, 클릭 수 등). Adobe Experience Platform으로 이동합니다. CRM과 같이 제3자 소스에서 인제스트된 데이터는 Adobe Experience Platform으로 직접 가져와야 합니다.

## Campaign Classic에서 내보내기 워크플로우 만들기

Campaign Classic에서 S3 또는 Azure Blob 저장소 위치로 데이터를 내보내려면 내보낼 데이터를 대상으로 하는 작업 과정을 만들어 저장소 위치로 보내야 합니다.

이렇게 하려면 다음을 추가하고 구성합니다.

* 타깃팅된 데이터를 CSV 파일로 추출하는 **[!UICONTROL Data extraction (file)]** 활동. 이 활동을 구성하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/extraction--file-.md)을 참조하십시오.

   ![](assets/rtcdp-extract-file.png)

* CSV 파일을 저장소 위치로 전송하는 **[!UICONTROL File transfer]** 활동. 이 활동을 구성하는 방법에 대한 자세한 내용은 [이 섹션](../../workflow/using/file-transfer.md)을 참조하십시오.

   ![](assets/rtcdp-file-transfer.png)

예를 들어 아래 워크플로우는 정기적으로 로그를 CSV 파일로 추출한 다음 파일을 저장 위치로 전송합니다.

![](assets/aep-export.png)

## 스토리지 위치를 소스로 연결

Adobe 경험 플랫폼의 **소스**&#x200B;로 S3 또는 Azure blob 저장소 위치를 연결하는 기본 단계는 아래에 나열되어 있습니다. 이러한 각 단계에 대한 자세한 내용은 [소스 커넥터 설명서](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)에서 확인할 수 있습니다.

1. Adobe Experience Platform **[!UICONTROL Sources]** 메뉴에서 스토리지 위치에 대한 연결을 만듭니다.

   * [Amazon S3 소스 연결 만들기](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/cloud-storage/s3.html)
   * [Azure Blob 커넥터](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/cloud-storage/blob.html)

   >[!NOTE]
   >
   >저장소 위치는 Amazon S3, 암호가 있는 SFTP, SSH 키가 있는 SFTP 또는 Azure Blob 연결일 수 있습니다. Adobe Campaign으로 데이터를 보내는 기본 방법은 Amazon S3 또는 Azure Blob을 통해 입니다.

   ![](assets/rtcdp-connector.png)

1. 클라우드 저장소 일괄 연결을 위한 데이터 흐름 구성 데이터 흐름(Dataflow)은 저장소 위치에서 Adobe Experience Platform 데이터 집합으로 데이터를 검색하고 인제스트하는 예약된 작업입니다. 이 단계를 통해 데이터 선택 및 CSV 필드의 XDM 스키마에 대한 매핑을 포함하여 저장소 위치에서 데이터 수집을 구성할 수 있습니다.

   자세한 내용은 [이 페이지](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/dataflow/cloud-storage.html)에서 확인할 수 있습니다.

   ![](assets/rtcdp-map-xdm.png)

1. 소스가 구성되면 Adobe Experience Platform은 사용자가 제공한 저장 위치에서 파일을 가져옵니다.

   이 작업은 필요에 따라 예약할 수 있습니다. 인스턴스에 이미 있는 로드에 따라 하루에 최대 6회까지 내보내기를 수행하는 것이 좋습니다.
