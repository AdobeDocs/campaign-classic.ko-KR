---
title: 워크플로우 데이터 사용 방법
seo-title: 워크플로우 데이터 사용 방법
description: 워크플로우 데이터 사용 방법
seo-description: null
page-status-flag: never-activated
uuid: ed03f14b-1b53-426e-9213-22cb2f3deb19
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: ec3844ca-8d80-4ddc-b08c-f18a6919bb28
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 워크플로우 데이터 사용 방법{#how-to-use-workflow-data}

## 데이터베이스 업데이트 {#updating-the-database}

수집된 모든 데이터를 사용하여 데이터베이스를 업데이트하거나 전달에 사용할 수 있습니다. 예를 들어 메시지 컨텐츠 개인화 가능성 강화(메시지에 계약 수 포함, 지난 1년 동안 평균 장바구니 지정 등) 또는 세부 인구 타겟팅(계약 공동 보유자에게 메시지 전송, 온라인 서비스 등 1,000명의 우수 가입자 타깃팅) 이 데이터를 목록으로 내보내거나 보관할 수도 있습니다.

### 목록 및 직접 업데이트 {#lists-and-direct-updates}

Adobe Campaign 데이터베이스 및 기존 목록의 데이터는 두 개의 전용 활동을 사용하여 업데이트할 수 있습니다.

* 이 **[!UICONTROL List update]** 활동을 통해 작업표를 날짜 목록에 저장할 수 있습니다.

   기존 목록을 선택하거나 만들 수 있습니다. 이 경우 이름과 레코드 폴더가 계산될 수 있습니다.

   ![](assets/s_user_create_list.png)

   목록 업데이트를 [참조하십시오](../../workflow/using/list-update.md).

* 이 **[!UICONTROL Update data]** 활동은 데이터베이스의 필드를 대량으로 업데이트합니다.

   자세한 내용은 데이터 [업데이트를](../../workflow/using/update-data.md)참조하십시오.

### 구독/구독 취소 관리 {#subscription-unsubscription-management}

워크플로우를 통해 수신자의 정보 서비스 가입 및 가입 해지에 대한 자세한 내용은 구독 서비스를 [참조하십시오](../../workflow/using/subscription-services.md).

## 워크플로우를 통해 전송 {#sending-via-a-workflow}

### 배달 활동 {#delivery-activity}

배달 활동은 게재에서 자세히 [설명합니다](../../workflow/using/delivery.md).

### 전달 강화 및 타깃팅 {#enriching-and-targeting-deliveries}

전달은 컨텐츠를 사용자 정의하기 위해 또는 대상 모집단 선택 프레임워크에서 워크플로우의 데이터를 처리할 수 있습니다.

예를 들어, DM 전달의 프레임워크 내에서 워크플로우에서 수행한 데이터 조작에서 얻은 추가 데이터를 추출 파일에 포함시킬 수 있습니다.

![](assets/s_advuser_add_data_postal_mail.png)

일반적인 개인화 필드 외에도 워크플로우 단계에서 전달 컨텐츠에 개인화 필드를 추가할 수 있습니다. 워크플로우 활동에 정의된 추가 데이터는 아래 예와 같이 배달 마법사에서 보관되고 액세스 가능하게 하여 DM 배달 프레임워크 내에서 출력 파일의 이름을 정의할 수 있습니다.

![](assets/s_advuser_using_additional_data.png)

워크플로우 테이블에 포함된 데이터는 해당 이름으로 식별됩니다.항상 targetData **링크로 구성됩니다** . 자세한 내용은 Target [데이터를](../../workflow/using/executing-a-workflow.md#target-data)참조하십시오.

이메일 전달 프레임워크 내에서 개인화 필드는 아래 예와 같이 타깃팅 워크플로우 단계에서 수행된 대상 확장의 데이터를 사용할 수도 있습니다.

![](assets/s_advuser_add_data_email.png)

세그먼트 코드가 타깃팅 활동에 지정된 경우, 이것은 워크플로우 테이블의 특정 열에 추가되며 개인화 필드와 함께 제공됩니다. 모든 개인화 필드를 표시하려면 개인화 단추를 통해 액세스할 수 있는 **[!UICONTROL Target extension > Other...]** 링크를 클릭합니다.

![](assets/s_advuser_segment_code_select.png)

## 데이터 내보내기 {#exporting-data}

### 파일 압축 또는 암호화 {#zipping-or-encrypting-a-file}

Adobe Campaign을 사용하면 압축되거나 암호화된 파일을 내보낼 수 있습니다. 활동을 통해 내보내기를 정의할 때 **[!UICONTROL Data extraction (file)]** 압축 또는 암호화할 후처리를 정의할 수 있습니다.

다음을 수행할 수 있습니다.

* Adobe Campaign 설치가 Adobe에서 호스팅하는 경우:서버에 필요한 [유틸리티를](https://support.neolane.net) 설치하도록 지원부에 요청을 보냅니다.
* Adobe Campaign 설치가 온-프레미스 인 경우:사용할 유틸리티를 설치합니다(예:GPG, GZIP) 및 응용 프로그램 서버에 필요한 키(암호화 키)가 있습니다.

그런 다음 다음과 같은 명령이나 코드를 사용할 수 있습니다.

```
function encryptFile(file) {  
  var systemCommand = “gpg --encrypt --recipient  recipientToEncryptTo ” + file;  
  var result = execCommand(systemCommand, true); 
}
```

파일을 가져올 때 파일의 압축을 풀거나 암호를 해독할 수도 있습니다. 처리 [전에 파일 압축을 풀거나 해독을 참조하십시오](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing).
