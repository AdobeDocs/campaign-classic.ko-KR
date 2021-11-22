---
product: campaign
title: 파일 압축 해제 또는 암호 해독
description: 처리 전에 Campaign Classic에서 파일의 압축을 풀거나 암호를 해독하는 방법을 알아봅니다.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 1a79da3b-2abc-4bfc-a0ee-8471c478638d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 11%

---

# 파일 압축 해제 또는 암호 해독 {#unzipping-or-decrypting-a-file-before-processing}

![](../../assets/common.svg)

Adobe Campaign을 사용하면 압축되었거나 암호화된 파일을 가져올 수 있습니다. 에서 읽기 전에 [데이터 로드(파일)](../../workflow/using/data-loading--file-.md) 활동을 통해 압축을 풀거나 파일 암호를 해독하기 위한 사전 처리를 정의할 수 있습니다.

다음을 수행하십시오.

1. 를 사용하십시오 [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data) 공개/개인 키 쌍을 생성합니다.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 모든 관리 사용자가 액세스할 수 있습니다. 사용자에게 관리자 권한을 부여하는 단계는 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ko#discover-control-panel)에 자세히 설명되어 있습니다.
   >
   >인스턴스는 AWS에서 호스팅하고 최신 버전으로 업그레이드해야 합니다 [Gold Standard](../../rn/using/gs-overview.md) 빌드 또는 [최신 GA 빌드(21.1.3)](../../rn/using/latest-release.md). [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 사용 중인 버전을 확인하는 방법을 알아봅니다. 인스턴스가 AWS에서 호스팅되는지 확인하려면 [이 페이지](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)에 설명된 단계를 수행합니다.

1. Adobe Campaign 설치가 Adobe에 의해 호스팅되는 경우 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 서버에 필요한 유틸리티를 설치하도록 합니다.
1. Adobe Campaign의 설치를 온-프레미스하는 경우 사용할 유틸리티를 설치합니다(예: GPG, GZIP) 및 애플리케이션 서버에 필요한 키(암호화 키)가 포함되어 있습니다.

그런 다음 원하는 사전 처리 명령을 워크플로우에 사용할 수 있습니다.

1. 추가 및 구성 **[!UICONTROL File transfer]** 활동 을 만들 수 있습니다.
1. 추가 **[!UICONTROL Data loading (file)]** 활동을 수행하고 파일 형식을 정의합니다.
1. **[!UICONTROL Pre-process the file]** 옵션을 선택합니다.
1. 적용할 사전 처리 명령을 지정합니다.
1. 다른 활동을 추가하여 파일에서 오는 데이터를 관리합니다.
1. 워크플로우를 저장하고 실행합니다.

아래 사용 사례에는 예제가 나와 있습니다.

**관련 항목:**

* [데이터 로드(파일) 활동](../../workflow/using/data-loading--file-.md).
* [파일 압축 또는 암호화](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file).

## 사용 사례: Campaign 컨트롤 패널에서 생성된 키를 사용하여 암호화된 데이터 가져오기 {#use-case-gpg-decrypt}

이 사용 사례에서는 Campaign 컨트롤 패널에서 생성된 키를 사용하여 외부 시스템에서 암호화된 데이터를 가져오기 위한 워크플로우를 빌드합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#video)

이 사용 사례를 수행하는 단계는 다음과 같습니다.

1. 키 쌍(공개/개인)을 생성하려면 Campaign 컨트롤 패널을 사용합니다. 자세한 단계는 [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data).

   * 공개 키는 외부 시스템과 공유되며, 이 키를 사용하여 Campaign으로 전송할 데이터를 암호화합니다.
   * 개인 키는 들어오는 암호화된 데이터를 해독하는 데 Campaign Classic이 사용합니다.

   ![](assets/gpg_generate.png)

1. 외부 시스템에서 Campaign 컨트롤 패널에서 다운로드한 공개 키를 사용하여 Campaign Classic으로 가져올 데이터를 암호화합니다.

1. Campaign Classic에서 Campaign 컨트롤 패널을 통해 설치된 개인 키를 사용하여 암호화된 데이터를 가져오는 워크플로우를 빌드하고 암호를 해독합니다. 이를 위해 다음과 같이 워크플로우를 빌드합니다.

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 활동: 외부 소스에서 Campaign Classic으로 파일을 전송합니다. 이 예제에서는 SFTP 서버에서 파일을 전송하려고 합니다.
   * **[!UICONTROL Data loading (file)]** 활동: 파일의 데이터를 데이터베이스에 로드하고 Campaign 컨트롤 패널에서 생성된 개인 키를 사용하여 암호를 해독합니다.

1. 를 엽니다. **[!UICONTROL File transfer]** 활동을 지정한 후 암호화된 .gpg 파일을 가져올 외부 계정을 지정합니다.

   ![](assets/gpg_key_transfer.png)

   활동 구성 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/file-transfer.md).

1. 를 엽니다. **[!UICONTROL Data loading (file)]** 활동을 만든 다음 필요에 따라 구성합니다. 활동 구성 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/data-loading--file-.md).

   들어오는 데이터를 해독하기 위해 활동에 사전 처리 단계를 추가합니다. 이렇게 하려면 **[!UICONTROL Pre-process the file]** 옵션을 선택한 다음 이 암호 해독 명령을 복사하여 **[!UICONTROL Command]** 필드 :

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >이 예에서는 기본적으로 &quot;암호 구문&quot;인 Campaign 컨트롤 패널에 사용되는 암호를 사용합니다.
   >
   >이전에 고객 지원 요청을 통해 인스턴스에 이미 GPG 키가 설치되어 있는 경우 암호가 변경되었으며 기본적으로 다른 형태로 되어 있을 수 있습니다.

1. 클릭 **[!UICONTROL OK]** 활동 구성을 확인합니다.

1. 이제 워크플로우를 실행할 수 있습니다. 실행되면 워크플로우 로그에서 암호 해독이 실행되었고 파일의 데이터를 가져왔는지 확인할 수 있습니다.

   ![](assets/gpg_run.png)

## 튜토리얼 비디오 {#video}

이 비디오에서는 GPG 키를 사용하여 데이터를 해독하는 방법을 보여줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

추가 Campaign Classic 방법 비디오를 사용할 수 있습니다 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko).
