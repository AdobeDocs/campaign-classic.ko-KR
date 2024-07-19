---
product: campaign
title: 지원되지 않는 SMS 커넥터 마이그레이션
description: 지원되지 않는 SMS 커넥터를 Extended Generic SMPP 커넥터로 마이그레이션
feature: SMS, Upgrade
hidefromtoc: true
exl-id: 60acf80c-8506-410b-ab2c-4f67a5677b43
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 1%

---

# 지원되지 않는 SMS 커넥터를 Extended Generic SMPP 커넥터로 마이그레이션{#unsupported-connector-migration}



릴리스 20.2부터 레거시 커넥터는 사용되지 않습니다. 이 문서는 이전 시스템에서 여전히 실행 중인 커넥터를 권장 SMPP 커넥터로 마이그레이션하는 데 도움이 됩니다.

>[!CAUTION]
>
>이 마이그레이션은 필수는 아니지만 Adobe이 권장하며 지원되는 최신 소프트웨어 버전에서 실행 중인지 확인합니다.

## SMS 커넥터 정보 {#about-sms-connectors}

다음 커넥터는 릴리스 20.2부터 더 이상 사용되지 않습니다.

* **[!UICONTROL Generic SMPP]**(이진 모드를 지원하는 SMPP 버전 3.4)
* **[!UICONTROL Sybase365]**(SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

사용 중단되는 기능은 계속 사용 및 지원되지만 더 이상 향상되지 않습니다. **[!UICONTROL Extended generic SMPP]** 커넥터를 사용하는 것이 좋습니다.

더 이상 사용되지 않는 기능과 제거된 기능에 대한 자세한 내용은 이 [페이지](../../rn/using/deprecated-features.md)를 참조하세요.

이전 SMS 커넥터는 웹 프로세스를 오버로드하는 Java SMS 커넥터를 사용하고 있습니다. 새 **[!UICONTROL Extended Generic SMPP]** 커넥터로 마이그레이션하면 이 로드가 이를 지원할 수 있는 MTA로 이동합니다.

## Extended Generic SMPP 커넥터로 마이그레이션 {#migrating-extended-generic-smpp}

>[!CAUTION]
>
>매개 변수를 바꿀 수 있는 경우에도 **[!UICONTROL Extended Generic SMPP]** 커넥터를 구성하려면 공급업체에 문의하여 나머지 매개 변수를 채우는 데 필요한 정보를 제공해야 합니다. 자세한 정보는 이 [페이지](sms-protocol.md)를 참조하십시오.

먼저 새 **[!UICONTROL Extended Generic SMPP]** 외부 계정을 만들어야 매개 변수 일부를 바꿀 수 있습니다. 자세한 단계는 이 [페이지](sms-set-up.md#creating-an-smpp-external-account)에서 확인할 수 있습니다.

이제 이전 커넥터에 따라 새로 만든 **[!UICONTROL Extended Generic SMPP]** 외부 계정의 **[!UICONTROL Mobile]** 탭에서 매개 변수를 입력해야 합니다.

### 원본 커넥터에서 {#from-generic-connector}

**[!UICONTROL Generic]** 커넥터를 선택할 때는 각 상황에 맞는 사용자 지정 JavaScript 커넥터가 있어야 합니다.

이 커넥터가 이미 SMPP 프로토콜을 사용하고 있는 경우 **[!UICONTROL Extended Generic SMPP]** 커넥터로 마이그레이션할 수 있습니다. 그렇지 않은 경우 공급업체에 문의하여 SMPP 프로토콜을 지원하고 컨설턴트의 도움을 받아 새 커넥터를 설정하십시오.

**[!UICONTROL Generic]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 전환할 수 있습니다.

![](assets/smpp_generic.png)

**[!UICONTROL Connection Settings]** 탭에서:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 일반 SMPP 커넥터에서 {#from-generic-smpp-connector}

**[!UICONTROL Generic SMPP]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 전환할 수 있습니다.

![](assets/smpp_generic_2.png)

**[!UICONTROL Connection Settings]** 탭에서:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

**[!UICONTROL Mapping of Encoding]** 탭에서:

* **[!UICONTROL Outbound SMS coding]**

**[!UICONTROL SMSC specificities]** 탭에서:

* **[!UICONTROL Coding when sending]**&#x200B;은(는) **[!UICONTROL ID Format in MT acknowledgement]**&#x200B;에 해당합니다.
* **[!UICONTROL Coding when receiving]**&#x200B;은(는) **[!UICONTROL ID Format in the SR]**&#x200B;에 해당합니다.

### Sybase365 커넥터에서 {#from-sybase}

**[!UICONTROL Sybase365]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 전환할 수 있습니다.

![](assets/smpp_3.png)

**[!UICONTROL Connection Settings]** 탭에서:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### CLX 커넥터에서 {#from-clx}

**[!UICONTROL CLX]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 전환할 수 있습니다.

![](assets/smpp_4.png)

**[!UICONTROL Connection Settings]** 탭에서:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서:

* **[!UICONTROL Source number]**

**[!UICONTROL SMSC specificities]** 탭에서:

* **[!UICONTROL Coding when sending]**&#x200B;은(는) **[!UICONTROL ID Format in MT acknowledgement]**&#x200B;에 해당합니다.
* **[!UICONTROL Coding when receiving]**&#x200B;은(는) **[!UICONTROL ID Format in the SR]**&#x200B;에 해당합니다.

### Tele2 커넥터에서 {#from-tele2}

**[!UICONTROL Tele2]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 전환할 수 있습니다.

![](assets/smpp_6.png)

**[!UICONTROL Connection Settings]** 탭에서:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

**[!UICONTROL Mapping of Encoding]** 탭에서:

* **[!UICONTROL Outbound SMS coding]**

### O2 커넥터에서 {#from-O2}

**[!UICONTROL O2]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 전환할 수 있습니다.

![](assets/smpp_5.png)

**[!UICONTROL Connection Settings]** 탭에서:

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서:

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**
