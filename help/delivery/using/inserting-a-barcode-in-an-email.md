---
product: campaign
title: 이메일에 바코드 삽입
description: 이메일에 바코드 삽입
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Email Design
role: User
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# 이메일에 바코드 삽입{#insert-a-barcode-in-an-email}

바코드 생성 모듈을 사용하면 2D 바코드를 포함하여 많은 공통 표준을 준수하는 여러 유형의 바코드를 만들 수 있습니다.

고객 기준으로 정의한 값을 이용하여 바코드를 비트맵으로 동적으로 생성할 수 있다. 개인화된 바코드를 이메일 캠페인에 포함할 수 있습니다. 수신자는 메시지를 인쇄하고 발행 회사에 표시하여 검색할 수 있습니다(예: 체크아웃 시).

이메일에 바코드를 삽입하려면 표시하려는 콘텐츠에 커서를 놓은 다음 개인화 버튼을 클릭합니다. **[!UICONTROL Include > Barcode...]**&#x200B;을(를) 선택합니다.

![](assets/barcode_insert_14.png)

그런 다음 필요에 맞게 다음 요소를 구성합니다.

1. 바코드 유형을 선택합니다.

   * 1D 형식의 경우 Adobe Campaign에서 Codabar, Code 128, GS1-128(이전 EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET 및 Royal Mail(RM4SCC) 형식을 사용할 수 있습니다.

     1D 바코드의 예:

     ![](assets/barcode_insert_08.png)

   * DataMatrix 및 PDF417 유형은 2D 포맷과 관련이 있습니다.

     2D 바코드의 예:

     ![](assets/barcode_insert_09.png)

   * QR 코드를 삽입하려면 이 유형을 선택하고 적용할 오류 수정 비율을 입력합니다. 이 비율은 반복되는 정보의 양과 악화 허용 한도를 정의합니다.

     ![](assets/barcode_insert_06.png)

     QR 코드의 예:

     ![](assets/barcode_insert_12.png)

1. 이메일에 삽입할 바코드의 크기를 입력합니다. 크기를 구성하면 바코드의 크기를 x1에서 x10으로 늘리거나 줄일 수 있습니다.
1. **[!UICONTROL Value]** 필드를 사용하면 바코드의 값을 정의할 수 있습니다. 값은 특별 오퍼와 일치할 수 있으며 기준의 함수가 될 수 있습니다. 이 값은 고객에 연결된 데이터베이스 필드의 값이 될 수 있습니다.

   이 예에서는 수신자의 계정 번호가 추가된 EAN-8 유형 바코드를 보여 줍니다. 이 계정 번호를 추가하려면 **[!UICONTROL Value]** 필드 오른쪽에 있는 개인화 단추를 클릭하고 **[!UICONTROL Recipient > Account number]**&#x200B;을(를) 선택하십시오.

   ![](assets/barcode_insert_15.png)

1. **[!UICONTROL Height]** 필드를 사용하면 각 막대 사이의 간격을 변경하여 바코드의 너비를 변경하지 않고 바코드의 높이를 구성할 수 있습니다.

   바코드의 유형에 따라 제한적으로 항목을 제어할 수 없습니다. 바코드 값이 올바르지 않으면 바코드가 빨간색으로 표시되는 **미리 보기** 모드에서만 표시됩니다.

   >[!NOTE]
   >
   >바코드에 할당된 값은 유형에 따라 다릅니다. 예를 들어 EAN-8 형식에는 정확히 8개의 숫자가 있어야 합니다.
   >
   >**[!UICONTROL Value]** 필드 오른쪽에 있는 개인화 단추를 사용하면 값 자체 외에 데이터를 추가할 수 있습니다. 이렇게 하면 바코드 표준에서 허용하는 한 바코드가 강화됩니다.
   >
   >예를 들어, GS1-128 바코드를 사용하고 있고 값 외에 받는 사람의 계좌 번호를 입력하려면 개인화 단추를 클릭하고 **[!UICONTROL Recipient > Account number]**&#x200B;을(를) 선택합니다. 선택한 수신자의 계좌 번호를 올바르게 입력하면 바코드가 이를 고려합니다.

이러한 요소가 구성되면 이메일을 마무리하여 보낼 수 있습니다. 오류를 방지하려면 게재를 수행하기 전에 **[!UICONTROL Preview]** 탭을 클릭하여 콘텐츠가 올바르게 표시되는지 항상 확인하십시오.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>바코드의 값이 올바르지 않으면 비트맵이 빨간색으로 교차하여 표시됩니다.

![](assets/barcode_insert_11.png)
