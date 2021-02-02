---
solution: Campaign Classic
product: campaign
title: 파일 압축 또는 암호화
description: 처리하기 전에 Campaign Classic에서 파일을 압축 또는 암호화하는 방법을 알아봅니다.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 파일 {#zipping-or-encrypting-a-file} 압축 또는 암호화

Adobe Campaign을 사용하면 압축 또는 암호화된 파일을 내보낼 수 있습니다. **[!UICONTROL Data extraction (file)]** 활동을 통해 내보내기를 정의할 때 zip을 압축 또는 암호화할 후처리를 정의할 수 있습니다.

그렇게 하려면 다음을 수행하십시오.

1. [Campaign 컨트롤 패널](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)을 사용하여 인스턴스에 대한 GPG 키 쌍을 설치합니다.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 AWS를 통해 호스팅되는 모든 고객에게 제공됩니다(마케팅 인스턴스를 사내에 호스트하는 고객 제외).

1. Adobe Campaign 설치가 Adobe을 통해 호스팅되는 경우 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하여 서버에 필요한 유틸리티를 설치하도록 하십시오.
1. Adobe Campaign의 설치를 온-프레미스 경우 사용할 유틸리티를 설치합니다(예:GPG, GZIP) 및 응용 프로그램 서버에 필요한 키(암호화 키)가 있습니다.

그런 다음 활동의 **[!UICONTROL Script]** 탭 또는 **[!UICONTROL JavaScript code]** 활동에서 명령이나 코드를 사용할 수 있습니다. 아래의 사용 사례에는 예가 나와 있습니다.

**관련 항목:**

* [처리하기 전에 파일 압축 해제 또는 해독](../../platform/using/unzip-decrypt.md)
* [데이터 추출(파일) 활동](../../workflow/using/extraction--file-.md).

## 사용 사례:Campaign 컨트롤 패널 {#use-case-gpg-encrypt}에 설치된 키를 사용하여 데이터 암호화 및 내보내기

이 경우 Campaign 컨트롤 패널에 설치된 키를 사용하여 데이터를 암호화하고 내보낼 수 있는 워크플로우를 구축합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#video)

이 사용 사례를 수행하는 단계는 다음과 같습니다.

1. GPG 유틸리티를 사용하여 GPG 키 쌍(공개/비공개)을 생성한 다음 공개 키를 Campaign 컨트롤 패널에 설치합니다. 자세한 단계는 [Campaign 컨트롤 패널 설명서](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)에서 확인할 수 있습니다.

1. Campaign Classic에서 Campaign 컨트롤 패널을 통해 설치된 개인 키를 사용하여 데이터를 내보내고 암호화하는 워크플로우를 구성합니다. 이렇게 하려면 다음과 같이 워크플로우를 구성합니다.

   ![](assets/gpg-workflow-encrypt.png)

   * **[!UICONTROL Query]** 활동:이 예제에서는 내보낼 데이터베이스의 데이터를 대상으로 하는 쿼리를 실행하려고 합니다.
   * **[!UICONTROL Data extraction (file)]** 활동:데이터를 파일로 추출합니다.
   * **[!UICONTROL JavaScript code]** 활동:추출할 데이터를 암호화합니다.
   * **[!UICONTROL File transfer]** 활동:외부 소스(이 예에서는 SFTP 서버)로 데이터를 보냅니다.

1. 데이터베이스에서 원하는 데이터를 타깃팅하도록 **[!UICONTROL Query]** 활동을 구성합니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/query.md)을 참조하십시오.

1. **[!UICONTROL Data extraction (file)]** 활동을 연 다음 필요에 따라 구성합니다. 활동을 구성하는 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/extraction--file-.md)에서 사용할 수 있습니다.

   ![](assets/gpg-data-extraction.png)

1. **[!UICONTROL JavaScript code]** 활동을 연 다음 아래 명령을 복사하여 붙여넣어 추출할 데이터를 암호화합니다.

   >[!IMPORTANT]
   >
   >명령에서 **지문** 값을 Campaign 컨트롤 패널에 설치된 공개 키의 지문으로 바꾸십시오.

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

1. **[!UICONTROL File transfer]** 활동을 연 다음 파일을 보낼 SFTP 서버를 지정합니다. 활동을 구성하는 방법에 대한 글로벌 개념은 [이 섹션](../../workflow/using/file-transfer.md)에서 사용할 수 있습니다.

   ![](assets/gpg-file-transfer.png)

1. 이제 워크플로우를 실행할 수 있습니다. 쿼리가 실행되면 쿼리별 데이터 대상이 SFTP 서버로 암호화된 .gpg 파일로 내보내집니다.

## 자습서 비디오 {#video}

이 비디오에서는 GPG 키를 사용하여 데이터를 암호화하는 방법을

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
