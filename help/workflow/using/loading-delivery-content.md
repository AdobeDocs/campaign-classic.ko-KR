---
product: campaign
title: 게재 콘텐츠 로드
description: 게재 콘텐츠 로드
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: a52baffd-402b-4b33-ab72-ac954e4dee85
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---

# 게재 콘텐츠 로드{#loading-delivery-content}

![](../../assets/common.svg)

게재 컨텐츠가 Amazon S3, FTP 또는 SFTP 서버에 있는 HTML 파일에서 사용할 수 있는 경우 Adobe Campaign 게재에 이 컨텐츠를 쉽게 로드할 수 있습니다.

방법은 다음과 같습니다.

1. Adobe Campaign과 콘텐츠 파일을 호스팅하는 (S)FTP 서버 간의 연결을 아직 정의하지 않은 경우 다음을 통해 새 S3, FTP 또는 SFTP 외부 계정을 만드십시오 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**. S3 또는 (S)FTP 서버에 대한 연결을 설정하는 데 사용되는 주소와 자격 증명을 이 외부 계정에 지정합니다.

   다음은 S3 외부 계정의 예입니다.

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 예를 들어 새 워크플로우를 만듭니다. **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. 추가 **[!UICONTROL File transfer]** 활동을 워크플로우에 추가하고

   * S3 또는 (S)FTP 서버에 연결하는 데 사용할 외부 계정입니다.
   * S3 또는 (S)FTP 서버에 있는 파일의 경로입니다.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. 추가 **[!UICONTROL Delivery]** 활동 및 를 아웃바운드 전환 **[!UICONTROL File transfer]** 활동. 다음과 같이 구성합니다.

   * 배달: 필요에 따라 시스템에서 이미 생성된 특정 게재이거나 기존 템플릿을 기반으로 새 게재일 수 있습니다.
   * 수신자: 이 예에서는 대상이 게재 자체에 지정된 것으로 간주됩니다.
   * 컨텐츠: 콘텐츠를 이전 활동에서 가져오더라도 **[!UICONTROL Specified in the delivery]**. 컨텐츠는 원격 서버에 있는 파일에서 직접 가져오므로 워크플로우에서 처리할 때 식별자가 없으며 인바운드 이벤트에서 온 것으로 식별할 수 없습니다.
   * 수행할 작업: 선택 **[!UICONTROL Save]** 게재를 저장하고 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** 워크플로우가 실행되면 됩니다.

   ![](assets/delivery_loadcontent_activityexample.png)

1. 에서 **[!UICONTROL Script]** 의 탭 **[!UICONTROL Delivery]** 활동에서 다음 명령을 추가하여 가져온 파일의 컨텐츠를 게재에 로드합니다.

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 워크플로우를 저장하고 실행합니다. 로드된 컨텐츠가 있는 새 게재는에서 만들어집니다 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**.

>[!NOTE]
>
>SFTP 서버 사용에 대한 우수 사례 및 문제 해결 방법이 자세히 설명되어 있습니다 [이 페이지에서](../../platform/using/sftp-server-usage.md).
