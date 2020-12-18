---
solution: Campaign Classic
product: campaign
title: 워크플로우 데이터 사용 방법
description: 워크플로우 데이터 사용 방법 학습
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 49f3c123cb8e91b3a2a2a1eb6bd593a242b8bbfe
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 3%

---


# 워크플로우 데이터 사용 방법{#how-to-use-workflow-data}

## 데이터베이스 {#updating-the-database} 업데이트

수집된 모든 데이터는 데이터베이스를 업데이트하거나 배달에서 사용할 수 있습니다. 예를 들어 메시지 컨텐츠 개인화의 가능성(메시지에 계약 수 포함, 지난 1년간 평균 장바구니 지정 등)을 강화할 수 있습니다. 또는 세부 정보 모집단 타깃팅(계약 공동 보유자에게 메시지를 보내고, 온라인 서비스 등의 최고 구독자 1,000명을 타깃팅합니다.) 이 데이터를 목록에서 내보내거나 보관할 수도 있습니다.

### 목록 및 직접 업데이트 {#lists-and-direct-updates}

Adobe Campaign 데이터베이스 및 기존 목록의 데이터는 2개의 전용 활동을 사용하여 업데이트할 수 있습니다.

* **[!UICONTROL List update]** 활동을 사용하면 작업표를 데이터목록에 저장할 수 있습니다.

   기존 목록을 선택하거나 만들 수 있습니다. 이 경우 이름과 레코드 폴더가 계산될 수 있습니다.

   ![](assets/s_user_create_list.png)

   [목록 업데이트](../../workflow/using/list-update.md)를 참조하십시오.

* **[!UICONTROL Update data]** 활동은 데이터베이스의 필드를 대량으로 업데이트합니다.

   자세한 내용은 [데이터 업데이트](../../workflow/using/update-data.md)를 참조하십시오.

### 구독/구독 취소 관리 {#subscription-unsubscription-management}

워크플로우를 통해 받는 사람을 정보 서비스에 가입 및 가입 취소하는 방법에 대한 자세한 내용은 [구독 서비스](../../workflow/using/subscription-services.md)를 참조하십시오.

## 워크플로우 {#sending-via-a-workflow}을(를) 통해 전송

### 배달 활동 {#delivery-activity}

배달 활동은 [배달](../../workflow/using/delivery.md)에 자세히 설명되어 있습니다.

### 제공 중단 및 타깃팅 {#enriching-and-targeting-deliveries}

게재는 컨텐츠를 사용자 정의하거나 타겟 모집단 선택 프레임워크에서 컨텐츠를 처리하기 위해 워크플로우의 데이터를 처리할 수 있습니다.

예를 들어, DM 전달의 프레임워크 내에서 워크플로우에서 수행한 데이터 조작에서 얻은 추가 데이터를 추출 파일에 포함시킬 수 있습니다.

![](assets/s_advuser_add_data_postal_mail.png)

일반적인 개인화 필드 외에도 워크플로우 단계에서 전달 컨텐츠에 개인화 필드를 추가할 수 있습니다. 워크플로우 활동에 정의된 추가 데이터는 아래 예와 같이 DM 전달 프레임워크 내의 출력 파일 이름을 정의하기 위해 전달 마법사에서 보관하여 액세스할 수 있습니다.

![](assets/s_advuser_using_additional_data.png)

워크플로우 테이블에 포함된 데이터는 해당 이름으로 식별됩니다.이것은 항상 **targetData** 링크로 구성됩니다. 자세한 내용은 [Target 데이터](../../workflow/using/data-life-cycle.md#target-data)를 참조하십시오.

이메일 전달 프레임워크 내에서 개인화 필드는 아래 예와 같이 타깃팅 워크플로우 단계에서 수행된 대상 확장의 데이터를 사용할 수도 있습니다.

![](assets/s_advuser_add_data_email.png)

세그먼트 코드가 타깃팅 활동에 지정된 경우, 이 코드는 워크플로우 테이블의 특정 열에 추가되고 개인화 필드와 함께 제공됩니다. 모든 개인화 필드를 표시하려면 개인화 단추를 통해 액세스할 수 있는 **[!UICONTROL Target extension > Other...]** 링크를 클릭합니다.

![](assets/s_advuser_segment_code_select.png)

## 데이터 내보내기 {#exporting-data}

### 파일 {#zipping-or-encrypting-a-file} 압축 또는 암호화

Adobe Campaign을 사용하면 압축 또는 암호화된 파일을 내보낼 수 있습니다. **[!UICONTROL Data extraction (file)]** 활동을 통해 내보내기를 정의할 때 zip을 압축 또는 암호화할 후처리를 정의할 수 있습니다.

그렇게 하려면 다음을 수행하십시오.

1. [Campaign 컨트롤 패널](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/gpg-keys-management.html#encrypting-data)을 사용하여 인스턴스에 대한 GPG 키 쌍을 설치합니다.

   >[!NOTE]
   >
   >Campaign 컨트롤 패널은 AWS를 통해 호스팅되는 모든 고객에게 제공됩니다(마케팅 인스턴스를 사내에 호스트하는 고객 제외).

1. Adobe Campaign 설치가 Adobe을 통해 호스팅되는 경우 Adobe 고객 지원 센터에 문의하여 서버에 필요한 유틸리티를 설치하도록 하십시오.
1. Adobe Campaign의 설치를 온-프레미스 경우 사용할 유틸리티를 설치합니다(예:GPG, GZIP) 및 응용 프로그램 서버에 필요한 키(암호화 키)가 있습니다.

그런 다음 활동의 **[!UICONTROL Script]** 탭 또는 **[!UICONTROL JavaScript code]** 활동에서 명령이나 코드를 사용할 수 있습니다. 아래의 사용 사례에는 예가 나와 있습니다.

**관련 항목:**

* [처리하기 전에 파일 압축 해제 또는 해독](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)
* [데이터 추출(파일) 활동](../../workflow/using/extraction--file-.md).

### 사용 사례:Campaign 컨트롤 패널 {#use-case-gpg-encrypt}에 설치된 키를 사용하여 데이터 암호화 및 내보내기

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

### 자습서 비디오 {#video}

이 비디오에서는 GPG 키를 사용하여 데이터를 암호화하는 방법을

>[!VIDEO](https://video.tv.adobe.com/v/36399?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
