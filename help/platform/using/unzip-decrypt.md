---
product: campaign
title: 파일 압축 해제 또는 암호 해독
description: 처리하기 전에 Campaign에서 파일의 압축을 풀거나 암호를 해독하는 방법을 알아봅니다
feature: Workflows
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 11%

---

# 파일 압축 풀기 또는 암호 해독 {#unzipping-or-decrypting-a-file-before-processing}



Adobe Campaign을 사용하면 압축 또는 암호화된 파일을 가져올 수 있습니다. 다음 위치에서 읽기 전 [데이터 로드 중(파일)](../../workflow/using/data-loading--file-.md) 활동을 수행하면 압축을 풀거나 파일의 암호를 해독하는 전처리 과정을 정의할 수 있습니다.

다음을 수행할 수 있습니다.

1. 사용 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) 공개/개인 키 쌍을 생성합니다.

   >[!NOTE]
   >
   >컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.
   >
   >인스턴스는 AWS에서 호스팅되어야 하며 [최신 GA 빌드](../../rn/using/rn-overview.md). [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 사용 중인 버전을 확인하는 방법을 알아봅니다. 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=ko)에 설명된 단계를 수행합니다.

1. Adobe Campaign 설치가 Adobe에 의해 호스팅되는 경우 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 필요한 유틸리티를 서버에 설치합니다.
1. Adobe Campaign 설치가 온프레미스에 있는 경우 사용할 유틸리티(예: GPG, GZIP)와 애플리케이션 서버에 필요한 키(암호화 키)를 설치합니다.

그런 다음 원하는 전처리 명령을 워크플로우에 사용할 수 있습니다.

1. 추가 및 구성 **[!UICONTROL File transfer]** 워크플로우의 활동.
1. 추가 **[!UICONTROL Data loading (file)]** 활동을 실행하고 파일 형식을 정의합니다.
1. **[!UICONTROL Pre-process the file]** 옵션을 선택합니다.
1. 적용할 전처리 명령을 지정합니다.
1. 다른 활동을 추가하여 파일에서 오는 데이터를 관리합니다.
1. 워크플로우를 저장하고 실행합니다.

아래 사용 사례에 예가 나와 있습니다.

**관련 항목:**

* [데이터 로드(파일) 활동](../../workflow/using/data-loading--file-.md).
* [파일 압축 또는 암호화](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## 사용 사례: Campaign 컨트롤 패널에서 생성한 키를 사용하여 암호화된 데이터 가져오기 {#use-case-gpg-decrypt}

이 사용 사례에서는 Campaign 컨트롤 패널에서 생성된 키를 사용하여 외부 시스템에서 암호화된 데이터를 가져오기 위한 워크플로우를 빌드합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#video)

이 사용 사례를 수행하는 단계는 다음과 같습니다.

1. Campaign 컨트롤 패널을 사용하여 키 쌍(공개/비공개)을 생성합니다. 자세한 단계는에서 확인할 수 있습니다. [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * 공개 키는 외부 시스템과 공유되며, 외부 시스템은 이 키를 사용하여 Campaign으로 전송할 데이터를 암호화합니다.
   * 개인 키는 Campaign Classic이 들어오는 암호화된 데이터를 해독하는 데 사용됩니다.

   ![](assets/gpg_generate.png)

1. 외부 시스템에서는 Campaign 컨트롤 패널에서 다운로드한 공개 키를 사용하여 데이터를 암호화하여 Campaign Classic으로 가져옵니다.

1. Campaign Classic에서 암호화된 데이터를 가져오고 Campaign 컨트롤 패널을 통해 설치된 개인 키를 사용하여 해독하는 워크플로우를 빌드합니다. 이를 위해 다음과 같은 워크플로우를 빌드합니다.

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 활동: 파일을 외부 소스에서 Campaign Classic으로 전송합니다. 이 예에서는 SFTP 서버에서 파일을 전송하려고 합니다.
   * **[!UICONTROL Data loading (file)]** 활동: 파일에서 데이터베이스로 데이터를 로드하고 Campaign 컨트롤 패널에서 생성된 개인 키를 사용하여 해독합니다.

1. 를 엽니다. **[!UICONTROL File transfer]** 그런 다음 암호화된 .gpg 파일을 가져올 외부 계정을 지정합니다.

   ![](assets/gpg_key_transfer.png)

   활동을 구성하는 방법에 대한 전체적인 개념은에서 사용할 수 있습니다. [이 섹션](../../workflow/using/file-transfer.md).

1. 를 엽니다. **[!UICONTROL Data loading (file)]** 활동을 구성한 다음 필요에 따라 구성합니다. 활동을 구성하는 방법에 대한 전체적인 개념은에서 사용할 수 있습니다. [이 섹션](../../workflow/using/data-loading--file-.md).

   들어오는 데이터를 해독하기 위해 활동에 전처리 단계를 추가합니다. 이렇게 하려면 **[!UICONTROL Pre-process the file]** 옵션을 선택한 다음 **[!UICONTROL Command]** 필드 :

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >이 예제에서는 Campaign 컨트롤 패널에서 기본적으로 사용되는 암호, 즉 &quot;passphrase&quot;를 사용합니다.
   >
   >과거에 고객 지원 센터 요청을 통해 인스턴스에 GPG 키를 이미 설치한 경우 암호가 변경되었을 수 있으며 기본적으로 암호와 다릅니다.

1. 클릭 **[!UICONTROL OK]** 활동 구성을 확인합니다.

1. 이제 워크플로우를 실행할 수 있습니다. 일단 실행되면 워크플로우 로그에서 암호 해독이 실행되었고 파일의 데이터를 가져왔는지 확인할 수 있습니다.

   ![](assets/gpg_run.png)

## 튜토리얼 비디오 {#video}

이 비디오는 GPG 키를 사용하여 데이터를 해독하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
