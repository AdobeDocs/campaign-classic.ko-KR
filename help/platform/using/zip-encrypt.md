---
product: campaign
title: 파일 압축 또는 암호화
description: 처리하기 전에 Campaign에서 파일을 압축하거나 암호화하는 방법에 대해 알아봅니다
feature: Data Management, Encryption
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 4596638c-d75a-4e07-a2d8-5befcaad3430
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 5%

---

# 파일 압축 또는 암호화 {#zipping-or-encrypting-a-file}

Adobe Campaign을 사용하면 압축 또는 암호화된 파일을 내보낼 수 있습니다. **[!UICONTROL Data extraction (file)]** 활동을 통해 내보내기를 정의할 때 파일을 압축하거나 암호화하는 후 처리를 정의할 수 있습니다.

다음을 수행할 수 있습니다.

1. [Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)을(를) 사용하여 인스턴스에 대한 GPG 키 쌍을 설치합니다.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 관리자 사용자로만 제한되며 특정 Campaign 버전에만 사용할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=ko)
   >

1. Adobe Campaign 설치가 Adobe에 의해 호스팅되는 경우 [고객 지원 Adobe](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하여 서버에 필요한 유틸리티를 설치하십시오.
1. Adobe Campaign 설치가 온프레미스에 있는 경우 사용할 유틸리티(예: GPG, GZIP)와 애플리케이션 서버에 필요한 키(암호화 키)를 설치합니다.

그런 다음 활동의 **[!UICONTROL Script]** 탭 또는 **[!UICONTROL JavaScript code]** 활동에서 명령 또는 코드를 사용할 수 있습니다. 아래 사용 사례에 예가 나와 있습니다.

**관련 항목:**

* [처리하기 전에 파일 압축 풀기 또는 암호 해독](../../platform/using/unzip-decrypt.md)
* [데이터 추출(파일) 활동](../../workflow/using/extraction-file.md).

## 사용 사례: Campaign 컨트롤 패널에 설치된 키를 사용하여 데이터 암호화 및 내보내기 {#use-case-gpg-encrypt}

이 사용 사례에서는 Campaign 컨트롤 패널에 설치된 키를 사용하여 데이터를 암호화하고 내보내기 위한 워크플로우를 빌드합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#video)

이 사용 사례를 수행하는 단계는 다음과 같습니다.

1. GPG 유틸리티를 사용하여 GPG 키 쌍(공개/비공개)을 생성한 다음 공개 키를 Campaign 컨트롤 패널에 설치합니다. 자세한 단계는 [Campaign 컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)에서 확인할 수 있습니다.

1. Campaign Classic에서 데이터를 내보내는 워크플로우를 빌드하고 Campaign 컨트롤 패널을 통해 설치된 개인 키를 사용하여 암호화합니다. 이를 위해 다음과 같은 워크플로우를 빌드합니다.

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 활동: 이 예제에서는 내보내려는 데이터베이스의 데이터를 대상으로 하는 쿼리를 실행하려고 합니다.
   * **[!UICONTROL Data extraction (file)]** 활동: 데이터를 파일로 추출합니다.
   * **[!UICONTROL JavaScript code]** 활동: 추출할 데이터를 암호화합니다.
   * **[!UICONTROL File transfer]** 활동: 외부 소스(이 예에서는 SFTP 서버)로 데이터를 보냅니다.

1. 데이터베이스에서 원하는 데이터를 타겟팅하도록 **[!UICONTROL Query]** 활동을 구성하십시오. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/query.md)을 참조하십시오.

1. **[!UICONTROL Data extraction (file)]** 활동을 연 다음 필요에 따라 구성합니다. 활동을 구성하는 방법에 대한 전체적인 개념은 [이 섹션](../../workflow/using/extraction-file.md)에서 확인할 수 있습니다.

   ![](assets/gpg-data-extraction.png)

1. **[!UICONTROL JavaScript code]** 활동을 연 다음 아래의 명령을 복사하여 붙여 넣어 추출할 데이터를 암호화합니다.

   >[!IMPORTANT]
   >
   >명령의 **fingerprint** 값을 Campaign 컨트롤 패널에 설치된 공개 키의 지문으로 바꾸십시오.

   ```
   var cmd='gpg ';
   cmd += ' --trust-model always';
   cmd += ' --batch --yes';
   cmd += ' --recipient fingerprint';
   cmd += ' --encrypt --output ' + vars.filename + '.gpg ' + vars.filename;
   execCommand(cmd,true);
   vars.filename=vars.filename + '.gpg'
   ```

   ![](assets/gpg-script.png)

1. **[!UICONTROL File transfer]** 활동을 연 다음 파일을 보낼 SFTP 서버를 지정합니다. 활동을 구성하는 방법에 대한 전체적인 개념은 [이 섹션](../../workflow/using/file-transfer.md)에서 확인할 수 있습니다.

   ![](assets/gpg-file-transfer.png)

1. 이제 워크플로우를 실행할 수 있습니다. 실행되면 쿼리의 데이터 대상이 SFTP 서버로 암호화된 .gpg 파일로 내보내집니다.

## 튜토리얼 비디오 {#video}

이 비디오는에서 GPG 키를 사용하여 데이터를 암호화하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

추가 Campaign Classic 방법 비디오를 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
