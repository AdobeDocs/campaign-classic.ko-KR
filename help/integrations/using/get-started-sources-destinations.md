---
product: campaign
title: 소스 및 대상 시작
description: Adobe Experience Platform 소스 및 대상에 대해 자세히 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
exl-id: 8cee52c7-ea56-4701-8ebb-eb18afffea51
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 15%

---

# 소스 및 대상 작업 {#rtcdp}



## 소스 및 대상 정보

Adobe Experience Platform을 사용하면 Campaign Classic과 Adobe Real-time Customer Data Platform(RTCDP) 간에 데이터를 공유할 수 있습니다. 이를 통해 Campaign 워크플로우에서 Adobe Experience Platform 대상을 타깃팅한 다음, 전송, 열기 및 클릭과 같은 대상과 관련된 Adobe Real-time Customer Data Platform 데이터로 다시 보낼 수 있습니다.

* 사용 **대상**: Adobe Experience Platform의 대상을 Campaign Classic으로 수집 이를 통해 마케팅 캠페인에 대해 알려진 데이터와 알 수 없는 데이터를 활성화할 수 있습니다.
* 사용 **소스**, Campaign Classic 데이터(예: 전송, 열기, 클릭)를 Adobe Experience Platform으로 내보냅니다. 이를 통해 서로 다른 소스에서 수집한 데이터를 한 곳에 집중하여 더 많은 작업을 수행할 수 있습니다.

>[!IMPORTANT]
>
>이 통합을 수행하는 동안 Adobe Campaign 계약에 따라 SFTP 저장소 제한, 데이터베이스 저장소 제한 및 활성 프로필 제한을 기억하십시오.

Adobe Real-time Customer Data Platform, 대상 및 소스에 대한 자세한 개요는 다음 페이지를 참조하십시오.

* [Adobe 실시간 고객 데이터 플랫폼](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html?lang=ko)
* [대상 설명서](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=ko)
* [소스 설명서](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=ko)

## Adobe Experience Platform과 Campaign Classic 연결

Adobe Experience Platform과 Campaign Classic 간에 데이터를 공유하려면 먼저 Adobe Campaign as a에 연결해야 합니다 **대상**&#x200B;및 AWS S3 또는 Azure blob 저장 공간 위치를 로 연결합니다. **소스** Adobe experience Platform에서 생성합니다.

커넥터가 구성되면 워크플로우를 사용하여 데이터 가져오기를 설정하거나 Campaign Classic으로 내보낼 수 있습니다.

![](assets/rtcdp-schema.png)

이러한 가져오기 및 내보내기 프로세스를 설정하는 방법에 대한 자세한 내용은 다음 섹션을 참조하십시오.

* [Adobe Experience Platform 세그먼트를 Campaign에 수집](../../integrations/using/ingest-aep-data.md)
* [Campaign에서 Adobe Experience Platform으로 데이터 내보내기](../../integrations/using/export-campaign-data.md)
