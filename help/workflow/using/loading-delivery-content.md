---
solution: Campaign Classic
product: campaign
title: 게재 콘텐츠 로드
description: 게재 콘텐츠 로드
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 3%

---


# 게재 콘텐츠 로드{#loading-delivery-content}

배달 컨텐츠를 Amazon S3, FTP 또는 SFTP 서버에 있는 HTML 파일에서 사용할 수 있는 경우 이 컨텐츠를 Adobe Campaign 배달에 쉽게 로드할 수 있습니다.

방법은 다음과 같습니다.

1. Adobe Campaign과 콘텐트 파일을 호스팅하는 (S)FTP 서버 간의 연결을 아직 정의하지 않은 경우 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;에서 새 S3, FTP 또는 SFTP 외부 계정을 만듭니다. 이 외부 계정에서 S3 또는 (S)FTP 서버에 대한 연결을 설정하는 데 사용되는 주소와 자격 증명을 지정합니다.

   다음은 S3 외부 계정의 예입니다.

   ![](assets/delivery_loadcontent_filetransfertexamples3.png)

1. 예를 들어 **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**&#x200B;에서 새 워크플로우를 만듭니다.
1. 워크플로우에 **[!UICONTROL File transfer]** 활동을 추가하고

   * S3 또는 (S)FTP 서버에 연결하는 데 사용할 외부 계정.
   * S3 또는 (S)FTP 서버에 있는 파일의 경로입니다.

   ![](assets/delivery_loadcontent_filetransfertexample.png)

1. **[!UICONTROL Delivery]** 활동을 추가하고 **[!UICONTROL File transfer]** 활동의 아웃바운드 전환에 연결합니다. 다음과 같이 구성합니다.

   * 배달:필요에 따라 시스템에서 이미 만든 특정 배달이거나 기존 템플릿을 기반으로 새 배달일 수 있습니다.
   * 받는 사람:이 예에서는 대상이 배달 자체에 지정된 것으로 간주됩니다.
   * 컨텐츠:이전 활동에서 컨텐츠를 가져오더라도 **[!UICONTROL Specified in the delivery]**&#x200B;을 선택합니다. 콘텐트는 원격 서버에 있는 파일에서 직접 가져오므로 작업 과정에서 처리할 때 식별자가 없으며 인바운드 이벤트에서 오는 것으로 식별할 수 없습니다.
   * 수행할 작업:**[!UICONTROL Save]**&#x200B;을 선택하여 배달을 저장하고 워크플로우가 실행되면 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]**&#x200B;에서 액세스할 수 있습니다.

   ![](assets/delivery_loadcontent_activityexample.png)

1. **[!UICONTROL Delivery]** 활동의 **[!UICONTROL Script]** 탭에서 다음 명령을 추가하여 전달에서 가져온 파일의 컨텐츠를 로드합니다.

   ```
   delivery.content.md.source=loadFile(vars.filename)
   ```

   ![](assets/delivery_loadcontent_script.png)

1. 워크플로우를 저장하고 실행합니다. 로드된 내용이 포함된 새 배달이 **[!UICONTROL Campaign management]** > **[!UICONTROL Deliveries]** 아래에 만들어집니다.

>[!NOTE]
>
>SFTP 서버 사용에 대한 우수 사례 및 문제 해결은 이 페이지[에 자세히 설명되어 있습니다.](../../platform/using/sftp-server-usage.md)
