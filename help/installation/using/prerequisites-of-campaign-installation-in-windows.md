---
product: campaign
title: Windows에서 Campaign 설치 사전 요구 사항
description: Windows에서 Campaign 설치 사전 요구 사항
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: a7cf59cc-9260-4109-af4c-b2e2a9c999da
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Windows에서 Campaign 설치 시작 {#prerequisites-of-campaign-installation-in-windows}



Adobe Campaign 설치에 필요한 기술 구성 및 소프트웨어는 [호환성 매트릭스](../../rn/using/compatibility-matrix.md).

다중 인스턴스 사용을 위한 Adobe Campaign 서버 설치 프로세스는 아래에 설명되어 있습니다. [서버 설치](../../installation/using/installing-the-server.md).

주요 단계는 다음과 같습니다.

1. 응용 프로그램 서버를 설치하려면 다음을 참조하십시오. [설치 프로그램 실행](../../installation/using/installing-the-server.md#executing-the-installation-program).
1. 웹 서버와 통합(선택 사항, 배포된 구성 요소에 따라)은 다음을 참조하십시오. [IIS 웹 서버 구성](../../installation/using/integration-into-a-web-server-for-windows.md#configuring-the-iis-web-server).

설치 단계가 완료되면 인스턴스, 데이터베이스 및 서버를 구성해야 합니다. 자세한 내용은 다음을 참조하십시오. [초기 구성 정보](../../installation/using/about-initial-configuration.md).

>[!NOTE]
>
>Adobe Campaign이 Windows 환경에 배포되면 필요한 액세스 권한이 있는 사용자는 네트워크에서 파일을 조작하는 동안 액세스 경로에 UNC 구문(Universal.Uniform Naming Convention)을 사용할 수 있습니다.
