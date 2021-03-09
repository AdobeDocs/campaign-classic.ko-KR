---
solution: Campaign Classic
product: campaign
title: 지원되지 않는 SMS 커넥터 마이그레이션
description: 지원되지 않는 SMS 커넥터를 확장 범용 SMPP 커넥터에 마이그레이션
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 584c11cc46d3a0cea3dcbbaef2700200fbdb8201
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 1%

---


# 지원되지 않는 SMS 커넥터를 확장 범용 SMPP 커넥터{#unsupported-connector-migration}(으)로 마이그레이션

릴리스 20.2부터 레거시 커넥터는 더 이상 사용되지 않습니다. 이 문서는 이전 시스템에서 실행 중인 커넥터를 권장 SMPP 커넥터로 마이그레이션하는 데 도움이 됩니다.

>[!CAUTION]
>
>이 마이그레이션은 필수는 아니지만 Adobe에서 권장되므로 지원되는 최신 버전의 소프트웨어를 사용하고 있는지 확인합니다.

## SMS 커넥터 정보 {#about-sms-connectors}

다음 커넥터는 릴리스 20.2부터 사용되지 않습니다.

* **[!UICONTROL Generic SMPP]** (SMPP 버전 3.4 지원 바이너리 모드)
* **[!UICONTROL Sybase365]** (SAP SMS 365)
* **[!UICONTROL CLX Communications]**
* **[!UICONTROL Tele2]**
* **[!UICONTROL O2]**
* **[!UICONTROL iOS]**

더 이상 사용되지 않는 기능은 계속 사용할 수 있으며 지원되지만 더 이상 향상되지 않습니다. **[!UICONTROL Extended generic SMPP]** 커넥터를 사용하는 것이 좋습니다.

사용 중단되거나 제거된 기능에 대한 자세한 내용은 이 [페이지](../../rn/using/deprecated-features.md)를 참조하십시오.

이전 SMS 커넥터에서 웹 프로세스를 오버로드하는 Java SMS 커넥터를 사용하고 있습니다. 새 **[!UICONTROL Extended Generic SMPP]** 커넥터로 마이그레이션하면 이 로드를 지원할 수 있는 MTA로 이동합니다.

## 확장 범용 SMPP 커넥터 {#migrating-extended-generic-smpp}로 마이그레이션

>[!CAUTION]
>
>매개 변수를 교체할 수 있더라도 **[!UICONTROL Extended Generic SMPP]** 커넥터를 구성하려면 나머지 매개 변수를 채우는 데 필요한 정보를 제공하는 제공자와 상의해야 합니다. 자세한 정보는 이 [페이지](../../delivery/using/sms-protocol.md)를 참조하십시오.

먼저 새 **[!UICONTROL Extended Generic SMPP]** 외부 계정을 만든 다음 일부 매개 변수를 교체할 수 있습니다. 이 [페이지](../../delivery/using/sms-channel.md#creating-an-smpp-external-account)에서 자세한 단계를 찾을 수 있습니다.

이제 새로 만든 **[!UICONTROL Extended Generic SMPP]** 외부 계정의 **[!UICONTROL Mobile]** 탭에서 이전 커넥터에 따라 매개 변수를 입력해야 합니다.

### 범용 커넥터 {#from-generic-connector}에서

**[!UICONTROL Generic]** 커넥터를 선택할 때 각 상황에 맞는 맞춤형 JavaScript 커넥터가 있어야 합니다.

이 커넥터가 이미 SMPP 프로토콜을 사용하고 있다는 것을 알고 있으면 **[!UICONTROL Extended Generic SMPP]** 커넥터로 마이그레이션할 수 있습니다. 그렇지 않은 경우 제공업체에서 SMPP 프로토콜을 지원하는지 확인하고 컨설턴트의 도움을 받아 새 커넥터를 설정하십시오.

**[!UICONTROL Generic]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 이동할 수 있습니다.

![](assets/smpp_generic.png)

**[!UICONTROL Connection Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**

### 범용 SMPP 커넥터 {#from-generic-smpp-connector}에서

**[!UICONTROL Generic SMPP]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 이동할 수 있습니다.

![](assets/smpp_generic_2.png)

**[!UICONTROL Connection Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**

**[!UICONTROL Mapping of Encoding]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Outbound SMS coding]**

**[!UICONTROL SMSC specificities]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Coding when sending]** 에 해당함  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 에 해당함  **[!UICONTROL ID Format in the SR]**

### Sybase365 커넥터 {#from-sybase}에서

**[!UICONTROL Sybase365]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 이동할 수 있습니다.

![](assets/smpp_3.png)

**[!UICONTROL Connection Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

### CLX 커넥터 {#from-clx}에서

**[!UICONTROL CLX]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 이동할 수 있습니다.

![](assets/smpp_4.png)

**[!UICONTROL Connection Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Source number]**

**[!UICONTROL SMSC specificities]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Coding when sending]** 에 해당함  **[!UICONTROL ID Format in MT acknowledgement]**
* **[!UICONTROL Coding when receiving]** 에 해당함  **[!UICONTROL ID Format in the SR]**

### Tele2 커넥터에서 {#from-tele2}

**[!UICONTROL Tele2]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 이동할 수 있습니다.

![](assets/smpp_6.png)

**[!UICONTROL Connection Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**

**[!UICONTROL Mapping of Encoding]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Outbound SMS coding]**

### O2 커넥터에서 {#from-O2}

**[!UICONTROL O2]** 커넥터에서 새로 만든 **[!UICONTROL Extended SMPP]** 계정으로 이동할 수 있습니다.

![](assets/smpp_5.png)

**[!UICONTROL Connection Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Account]**
* **[!UICONTROL Password]**
* **[!UICONTROL Server]**
* **[!UICONTROL Port]**
* **[!UICONTROL System Type]**

**[!UICONTROL SMPP Channel Settings]** 탭에서 다음을 수행합니다.

* **[!UICONTROL Source number]**
* **[!UICONTROL Source NPI]**
* **[!UICONTROL Destination NPI]**
* **[!UICONTROL Source TON]**
* **[!UICONTROL Destination TON]**