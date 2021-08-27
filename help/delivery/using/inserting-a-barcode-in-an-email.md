---
product: campaign
title: 전자 메일에 바코드 삽입
description: 전자 메일에 바코드 삽입
audience: delivery
content-type: reference
topic-tags: sending-emails
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# 전자 메일에 바코드 삽입{#inserting-a-barcode-in-an-email}

![](../../assets/common.svg)

바코드 생성 모듈을 사용하면 2D 바코드를 포함하여 다양한 공통 표준을 준수하는 여러 종류의 바코드를 만들 수 있습니다.

고객 기준을 사용하여 정의된 값을 사용하여 바코드를 비트맵으로 동적으로 생성할 수 있습니다. 개인화된 바코드는 이메일 캠페인에 포함할 수 있습니다. 수신자는 메시지를 인쇄하여 스캔을 위해 발행 회사에 표시할 수 있습니다(예를 들어 체크 아웃할 때).

전자 메일에 바코드를 삽입하려면 커서를 표시할 콘텐츠에 놓고 개인화 단추를 클릭합니다. **[!UICONTROL Include > Barcode...]**&#x200B;을(를) 선택합니다.

![](assets/barcode_insert_14.png)

그런 다음 필요에 맞게 다음 요소를 구성합니다.

1. 바코드 유형을 선택합니다.

   * 1D 형식의 경우 Adobe Campaign에서 다음 유형을 사용할 수 있습니다. Codabar, Code 128, GS1-128(이전의 EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET 및 Royal Mail(RM4SCC).

      1D 바코드의 예:

      ![](assets/barcode_insert_08.png)

   * DataMatrix 및 PDF417 유형은 2D 포맷과 관련이 있습니다.

      2D 바코드의 예:

      ![](assets/barcode_insert_09.png)

   * QR 코드를 삽입하려면 이 유형을 선택하고 적용할 오류 수정 비율을 입력합니다. 이 비율은 반복되는 정보의 양과 열화에 대한 허용한도를 정의합니다.

      ![](assets/barcode_insert_06.png)

      QR 코드의 예:

      ![](assets/barcode_insert_12.png)

1. 전자 메일에 삽입할 바코드의 크기를 입력합니다. 스케일을 구성하면 바코드의 크기를 x1에서 x10으로 늘리거나 줄일 수 있습니다.
1. **[!UICONTROL Value]** 필드를 사용하면 바코드의 값을 정의할 수 있습니다. 값은 특별 오퍼와 일치할 수 있으며 기준의 기능일 수 있으며, 고객에 연결된 데이터베이스 필드의 값이 될 수 있습니다.

   이 예에서는 수신자의 계정 번호를 추가한 EAN-8 형식의 바코드를 보여 줍니다. 이 계정 번호를 추가하려면 **[!UICONTROL Value]** 필드 오른쪽에 있는 개인화 단추를 클릭하고 **[!UICONTROL Recipient > Account number]** 을 선택합니다.

   ![](assets/barcode_insert_15.png)

1. **[!UICONTROL Height]** 필드를 사용하면 각 막대 사이의 간격을 변경하여 바코드의 너비를 변경하지 않고 바코드의 높이를 구성할 수 있습니다.

   바코드 유형에 따라 제한적인 항목 제어가 없습니다. 바코드 값이 올바르지 않으면 바코드가 빨간색으로 교차되는 **미리 보기** 모드에서만 볼 수 있습니다.

   >[!NOTE]
   >
   >바코드에 할당된 값은 해당 유형에 따라 다릅니다. 예를 들어 EAN-8 유형은 정확히 8개의 숫자를 가집니다.
   >
   >**[!UICONTROL Value]** 필드 오른쪽의 개인화 단추를 사용하면 값 자체에 데이터를 추가할 수 있습니다. 바코드 표준이 바코드를 수락하는 경우 바코드를 강화합니다.
   >
   >예를 들어, GS1-128 유형 바코드를 사용하고 값 외에 수신자의 계정 번호를 입력하려면 개인화 버튼을 클릭하고 **[!UICONTROL Recipient > Account number]** 을 선택합니다. 선택한 수신자의 계좌 번호를 올바르게 입력하면 바코드가 이를 고려합니다.

이러한 요소가 구성되면 전자 메일을 완료하고 보낼 수 있습니다. 오류를 방지하려면 항상 **[!UICONTROL Preview]** 탭을 클릭하여 배달을 수행하기 전에 컨텐츠가 올바르게 표시되는지 확인하십시오.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>바코드의 값이 올바르지 않으면 비트맵이 빨간색으로 교차되어 표시됩니다.

![](assets/barcode_insert_11.png)
