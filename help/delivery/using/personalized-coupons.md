---
title: 개인화된 쿠폰
seo-title: 개인화된 쿠폰
description: 개인화된 쿠폰
seo-description: null
page-status-flag: never-activated
uuid: c840e2de-f0ef-478b-af9f-82e1b6534933
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: f324afa5-304c-470e-a592-290f76a11ccb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 개인화된 쿠폰{#personalized-coupons}

배달물에 쿠폰을 추가하면 받는 사람에게 제품 및 서비스에 대한 향상된 가치를 제공할 수 있습니다. 캠페인 쿠폰 모듈을 사용하여 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만들 수 있습니다. 배달을 만들 준비가 되면 해당 쿠폰을 지정합니다. 쿠폰은 특정 기간에 대해 유효하므로 지정된 쿠폰은 배달 메시지에 고유하게 연결됩니다. 또한 Campaign은 배달을 보내기 전에 메시지 수에 대한 쿠폰이 충분한지 확인합니다.

>[!NOTE]
>
>쿠폰 관리는 반드시 설치해야 하는 패키지입니다. 쿠폰 관리가 있는지 확인하려면 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>쿠폰 데이터는 CSV 및 XML 형식을 사용하여 가져오고 내보낼 수 있습니다. 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션을](../../platform/using/generic-imports-and-exports.md)참조하십시오.

## 쿠폰 만들기 {#creating-a-coupon}

쿠폰 모듈은 쿠폰을 만들 때 두 가지 옵션을 제공합니다.

* **익명**:선택한 받는 사람 또는 받는 사람 목록을 위한 일반 쿠폰입니다.
* **개인**:특정 수신자를 위한 개인화된 쿠폰

아래 단계를 수행하기 전에 만들려는 쿠폰 유형을 알고 있어야 합니다.

1. 캠페인 트리에서 로 **[!UICONTROL Resources > Campaign management > Coupons]**&#x200B;이동합니다.

   ![](assets/deliv_coup_01.png)

1. 단추를 **[!UICONTROL New]** 클릭합니다.
1. 쿠폰 이름을 **[!UICONTROL Label]** 필드에 입력합니다. 고유한 코드가 자동으로 입력되었습니다 **[!UICONTROL Coupon code]**. 코드를 유지하거나 새 코드를 입력할 수 있습니다.

   ![](assets/deliv_coup_02.png)

1. 쿠폰 유효 기간을 **[!UICONTROL Start date]** 선택하고 **[!UICONTROL End date]** 설정하려면 을 선택합니다.
1. 에서 **[!UICONTROL Coupon type]**[익명] 또는 [개인]을 선택합니다.

   **[!UICONTROL Anonymous coupons]** :익명의 쿠폰은 모든 받는 사람에게 동일합니다. 쿠폰 유형 **메뉴에서 익명 옵션을 선택했는지 확인하고 저장을** 클릭하여 **** 쿠폰을 생성합니다.

   **[!UICONTROL Individual coupons]** :개별 쿠폰은 추가 쿠폰 코드를 사용하여 개인화할 수 있습니다. 예를 들어, 스포츠 장비 스토어에서 판매할 수 있는 개별 쿠폰이 만들어집니다. 그러나 받는 사람 명단은 길고 한 종목에 대해서도 같은 열정을 갖고 있지 않다. 스포츠(예: 축구, 축구, 야구 등)를 기반으로 개별 쿠폰에 대한 코드 이름을 추가할 수 있습니다. 각 코드를 해당 수신자에게 보냅니다.

   1. [개인]을 선택하면 새 탭인 쿠폰이 왼쪽 아래에 나타납니다. 탭으로 이동한 후 을 클릭합니다 **[!UICONTROL Coupons]** . **[!UICONTROL Add]**
   1. 팝업 창의 메시지가 표시되면 개별 쿠폰에 대한 고유한 코드를 입력합니다.
   1. 을 **[!UICONTROL Save]** 클릭하여 쿠폰을 생성합니다.
   쿠폰 탭에 대한 자세한 내용은 개별 쿠폰 [구성을](#configuring-individual-coupons)참조하십시오.

   >[!NOTE]
   >
   >개별 쿠폰은 일괄 가져올 수 있습니다. 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션을](../../platform/using/generic-imports-and-exports.md)참조하십시오.

### 개별 쿠폰 구성 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

쿠폰 탭은 개별 쿠폰에서만 사용할 수 있습니다. 쿠폰이 게재와 연결된 후 쿠폰 탭에서는 다음 세부 정보를 제공합니다.

* **[!UICONTROL Status]** :쿠폰 사용 가능 여부.
* **[!UICONTROL Redeemed on]** :쿠폰 상환일
* **[!UICONTROL Channel]** :쿠폰을 보내는 데 사용된 채널입니다.
* **[!UICONTROL Address]** :받는 사람의 이메일 주소입니다.

및 에 대한 **[!UICONTROL status]**&#x200B;값이 자동으로 **[!UICONTROL channel]****[!UICONTROL address]** 완료됩니다. 그러나 에 대한 값은 Campaign에서 복구되지 **[!UICONTROL redeemed on]** 않습니다. 쿠폰 상환에 대한 세부 정보가 있는 파일을 가져와 완료할 수 있습니다.

## 이메일 전달에 쿠폰 삽입 {#inserting-a-coupon-into-an-email-delivery}

아래 예에서는 홈 페이지에서 배달이 만들어집니다. 배달을 만드는 방법에 대한 자세한 지침은 [이 섹션을](../../delivery/using/about-email-channel.md)참조하십시오. 워크플로우에서 배달에 쿠폰을 추가할 수도 있습니다.

1. 이동 **[!UICONTROL Campaigns]** 후 선택합니다 **[!UICONTROL Deliveries]**.
1. 클릭 **[!UICONTROL Create]**.

   ![](assets/deliv_coup_04.png)

1. 에 이름을 **[!UICONTROL Label]** 입력하고 을 클릭합니다 **[!UICONTROL Continue]**.
1. 수신자를 **[!UICONTROL To]** 추가하려면 을 클릭합니다.
1. 을 **[!UICONTROL Add]** 클릭하여 배달할 수신자를 선택합니다. 수신자를 선택한 후 을 클릭하여 **[!UICONTROL Ok]** 배달로 돌아갑니다.

   ![](assets/deliv_coup_05.png)

1. 제목을 입력하고 메시지에 컨텐츠를 추가합니다.

   ![](assets/deliv_coup_06.png)

1. 도구 모음에서 을 **[!UICONTROL Properties]** 클릭하고 **[!UICONTROL Advanced]** 탭을 선택합니다.
1. 폴더 아이콘을 **[!UICONTROL Coupon management]**&#x200B;클릭합니다.

   ![](assets/deliv_coup_07.png)

1. 쿠폰을 선택하고 을 **[!UICONTROL Ok]**&#x200B;클릭합니다. 다시 **[!UICONTROL Ok]** 클릭합니다.

   ![](assets/deliv_coup_08.png)

1. 메시지를 클릭하여 쿠폰을 배치할 위치를 선택합니다.

   ![](assets/deliv_coup_09.png)

1. 개인화 아이콘을 클릭하여 쿠폰 유형에 따라 다음 중 하나를 선택합니다.

   * 익명 쿠폰: **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 개별 쿠폰: **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      쿠폰은 지정된 이름이 아닌 코드로 메시지에 삽입됩니다. 코드는 Campaign 표준 데이터 모델 내에서 사용됩니다.
   ![](assets/deliv_coup_12.png)

1. 테스트를 실행하여 쿠폰에 할당한 이름을 확인합니다. 탭으로 이동한 후 을 클릭합니다 **[!UICONTROL Preview]** . **[!UICONTROL Test personalization]** 테스트에 사용할 수신자를 선택합니다.

   ![](assets/deliv_coup_13.png)

   테스트 후 쿠폰은 코드가 아닌 지정된 이름으로 표시되어야 합니다.

   ![](assets/deliv_coup_14.png)

1. 도구 모음에서 **[!UICONTROL Send]** (왼쪽 위)를 클릭하고 배달을 보낼 방법을 선택합니다.

   ![](assets/deliv_coup_15.png)

1. 클릭 **[!UICONTROL Analyze]**. 분석 로그에서 모든 받는 사람에 대한 쿠폰이 충분한지 확인한 경우 을 클릭하여 **[!UICONTROL Confirm delivery]** 보냅니다.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>배달할 쿠폰 부족 관리 방법에 대한 지침은 쿠폰 [부족 관리를 참조하십시오](#managing-insufficient-coupons)

배달이 성공했는지 확인하려면:

1. 로 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**&#x200B;이동합니다.
1. 탭을 **[!UICONTROL Deliveries]** 클릭합니다.

   ![](assets/deliv_coup_17.png)

   상태가 성공적으로 배달되도록 **[!UICONTROL Finished]** 표시됩니다.

>[!NOTE]
>
>기본적으로 쿠폰 관리 모듈은 **nms:recipient** 테이블을 사용합니다. 다른 테이블 사용 방법에 대한 지침은 스키마 [편집을 참조하십시오](../../configuration/using/data-schemas.md).

## 쿠폰 부족 관리 {#managing-insufficient-coupons}

메시지 수보다 쿠폰 수가 적으면 배달 분석이 중지됩니다. 이러한 경우 쿠폰을 더 가져오거나 메시지 수를 제한할 수 있습니다. 메시지 수를 제한하려면 아래 지침을 따르십시오.

1. 이메일 배달 창으로 이동합니다.
1. 클릭 **[!UICONTROL To]**.
1. 에서 **[!UICONTROL Select target]**&#x200B;탭으로 **[!UICONTROL Exclusions]** 이동합니다.

   ![](assets/deliv_coup_18.png)

1. 제외 설정 섹션에서 을 클릭합니다 **[!UICONTROL Edit]**.
1. 보낼 메시지 수를 **[!UICONTROL Limit delivery to...messages]** 입력하고 클릭합니다 **[!UICONTROL Ok]**. 배송을 보낼 수 있습니다

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>제한된 수의 쿠폰을 관리할 때 배달 워크플로우를 통해 기준에 따라 배달을 분할할 수 있습니다. 대상을 제한하지 않고 특정 모집단으로 쿠폰을 전송하려는 경우 좋은 옵션입니다.
