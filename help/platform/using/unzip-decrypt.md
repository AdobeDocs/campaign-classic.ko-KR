---
solution: Campaign Classic
product: campaign
title: 파일의 압축을 풀거나 해독합니다.
description: 처리하기 전에 Campaign Classic에서 파일의 압축을 풀거나 암호를 해독하는 방법을 알아봅니다.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 1cde12d33551206da12e03a7e8deb198d427ab3a
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 2%

---


# {#unzipping-or-decrypting-a-file-before-processing} 파일의 압축을 풀거나 해독합니다.

Adobe Campaign을 사용하면 압축 또는 암호화된 파일을 가져올 수 있습니다. [데이터 로드(파일)](../../workflow/using/data-loading--file-.md) 활동에서 읽으려면 먼저 사전 처리를 정의하여 파일을 압축 해제하거나 해독할 수 있습니다.

그렇게 하려면 다음을 수행하십시오.

1. 공개/비공개 키 쌍을 생성하려면 [Campaign 컨트롤 패널](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)을 사용합니다.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 AWS를 통해 호스팅되는 모든 고객에게 제공됩니다(마케팅 인스턴스를 사내에 호스트하는 고객 제외).

1. Adobe Campaign 설치가 Adobe을 통해 호스팅되는 경우 Adobe 고객 지원 센터에 문의하여 서버에 필요한 유틸리티를 설치하도록 하십시오.
1. Adobe Campaign의 설치를 온-프레미스 경우 사용할 유틸리티를 설치합니다(예:GPG, GZIP) 및 응용 프로그램 서버에 필요한 키(암호화 키)가 있습니다.

그런 다음 원하는 사전 처리 명령을 워크플로우에 사용할 수 있습니다.

1. 워크플로우에서 **[!UICONTROL File transfer]** 활동을 추가하고 구성합니다.
1. **[!UICONTROL Data loading (file)]** 활동을 추가하고 파일 형식을 정의합니다.
1. **[!UICONTROL Pre-process the file]** 옵션을 선택합니다.
1. 적용할 사전 처리 명령을 지정합니다.
1. 다른 활동을 추가하여 파일에서 가져오는 데이터를 관리합니다.
1. 워크플로우를 저장하고 실행합니다.

아래의 사용 사례에는 예가 나와 있습니다.

**관련 항목:**

* [데이터 로드(파일) 활동](../../workflow/using/data-loading--file-.md).
* [파일](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file) 압축 또는 암호화

## 사용 사례:Campaign 컨트롤 패널 {#use-case-gpg-decrypt}에서 생성된 키를 사용하여 암호화된 데이터 가져오기

이 경우 Campaign 컨트롤 패널에서 생성된 키를 사용하여 외부 시스템에서 암호화된 데이터를 가져오기 위한 워크플로우를 구축합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#video)

이 사용 사례를 수행하는 단계는 다음과 같습니다.

1. Campaign 컨트롤 패널을 사용하여 키 쌍(공개/비공개)을 생성합니다. 자세한 단계는 [Campaign 컨트롤 패널 설명서](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#decrypting-data)에서 확인할 수 있습니다.

   * 공개 키는 Campaign으로 전송할 데이터를 암호화하는 데 사용하는 외부 시스템과 공유됩니다.
   * 개인 키는 Campaign Classic에서 들어오는 암호화된 데이터를 해독하는 데 사용됩니다.

   ![](assets/gpg_generate.png)

1. 외부 시스템에서는 Campaign 컨트롤 패널에서 다운로드한 공개 키를 사용하여 Campaign Classic으로 가져올 데이터를 암호화합니다.

1. Campaign Classic에서 Campaign 컨트롤 패널을 통해 설치된 개인 키를 사용하여 암호화된 데이터를 가져오고 이를 해독하는 작업 과정을 만듭니다. 이렇게 하려면 다음과 같이 워크플로우를 구성합니다.

   ![](assets/gpg_import_workflow.png)

   * **[!UICONTROL File transfer]** 활동:외부 소스에서 Campaign Classic으로 파일을 전송합니다. 이 예에서는 SFTP 서버에서 파일을 전송하려고 합니다.
   * **[!UICONTROL Data loading (file)]** 활동:파일의 데이터를 데이터베이스에 로드하고 Campaign 컨트롤 패널에 생성된 개인 키를 사용하여 이를 해독합니다.

1. **[!UICONTROL File transfer]** 활동을 연 다음 암호화된 .gpg 파일을 가져올 외부 계정을 지정합니다.

   ![](assets/gpg_key_transfer.png)

   활동을 구성하는 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/file-transfer.md)에서 사용할 수 있습니다.

1. **[!UICONTROL Data loading (file)]** 활동을 연 다음 필요에 따라 구성합니다. 활동을 구성하는 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/data-loading--file-.md)에서 사용할 수 있습니다.

   들어오는 데이터의 암호를 해독하려면 사전 처리 단계를 활동에 추가합니다. 이렇게 하려면 **[!UICONTROL Pre-process the file]** 옵션을 선택한 다음 **[!UICONTROL Command]** 필드에 이 암호 해독 명령을 복사하여 붙여 넣습니다.

   `gpg --batch --passphrase passphrase --decrypt <%=vars.filename%>`

   ![](assets/gpg_load.png)

   >[!CAUTION]
   >
   >이 예에서는 기본적으로 &quot;암호 문구&quot;인 Campaign 컨트롤 패널에서 사용하는 암호를 사용합니다.
   >
   >이전에 고객 지원 요청을 통해 인스턴스에 이미 GPG 키가 설치되어 있는 경우 암호가 변경되었으며 기본적으로 다른 형태일 수 있습니다.

1. **[!UICONTROL OK]**&#x200B;을 클릭하여 활동 구성을 확인합니다.

1. 이제 워크플로우를 실행할 수 있습니다. 이 파일이 실행되면 워크플로우 로그에서 암호 해독이 실행되었고 파일의 데이터를 가져올 수 있습니다.

   ![](assets/gpg_run.png)

## 자습서 비디오 {#video}

이 비디오에서는 GPG 키를 사용하여 데이터를 해독하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/36482?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
