---
product: campaign
title: 개인화된 쿠폰
description: 개인화된 쿠폰을 만들고 삽입하는 방법을 알아봅니다
feature: Personalization
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '885'
ht-degree: 1%

---

# 개인화된 쿠폰{#personalized-coupons}

![](../../assets/v7-only.svg)

게재 시 쿠폰을 추가하면 수신자가 제품 및 서비스에 대해 향상된 가치를 제공할 수 있습니다. 캠페인 쿠폰 모듈을 사용하여 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만들 수 있습니다. 게재를 만들 준비가 되면 적용 가능한 쿠폰을 할당합니다. 쿠폰은 선택한 기간에 대해 유효하므로 지정된 쿠폰은 배달 메시지에 고유하게 연결됩니다. 또한 Campaign은 게재가 전송되기 전에 메시지 수에 대한 쿠폰이 충분한지 확인합니다.

>[!NOTE]
>
>쿠폰 관리는 설치해야 하는 패키지입니다. 쿠폰 관리 권한이 있는지 확인하려면 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**
>
>쿠폰 데이터는 CSV 및 XML 형식을 사용하여 가져오고 내보낼 수 있습니다. 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션](../../platform/using/get-started-data-import-export.md).

## 쿠폰 만들기 {#creating-a-coupon}

쿠폰 모듈은 쿠폰을 만들 때 두 가지 옵션을 제공합니다.

* **익명**: 일부 수신자 또는 수신자 목록을 위한 일반 쿠폰입니다.
* **개인**: 일부 수신자를 위한 개인화된 쿠폰입니다.

아래 단계를 수행하기 전에 만들 쿠폰 유형을 알고 있는지 확인하십시오.

1. 캠페인 트리에서 로 이동합니다. **[!UICONTROL Resources > Campaign management > Coupons]**.

   ![](assets/deliv_coup_01.png)

1. **[!UICONTROL New]** 버튼을 클릭합니다.
1. 쿠폰 이름을 입력합니다. **[!UICONTROL Label]** 필드. 고유한 코드가 자동으로 **[!UICONTROL Coupon code]**. 코드를 유지하거나 새 코드를 입력할 수 있습니다.

   ![](assets/deliv_coup_02.png)

1. 선택 **[!UICONTROL Start date]** 및 **[!UICONTROL End date]** 쿠폰이 유효한 기간을 설정하려면
1. in **[!UICONTROL Coupon type]**&#x200B;익명 또는 개인을 선택합니다.

   **[!UICONTROL Anonymous coupons]** : 익명 쿠폰은 모든 수신자에게 동일합니다. 에서 익명 이 선택되었는지 확인합니다. **쿠폰 유형** 메뉴를 클릭하고 **저장** 쿠폰 생성.

   **[!UICONTROL Individual coupons]** : 개별 쿠폰은 추가 쿠폰 코드를 사용하여 추가로 개인화할 수 있습니다. 예를 들어, 스포츠 장비 스토어에서 판매용으로 개별 쿠폰이 만들어집니다. 그러나 받는 사람 명단은 길고 한 종목에 대해서도 같은 열정을 갖고 있지 않다. 스포츠(예: 축구, 축구, 야구 등)를 기반으로 개별 쿠폰에 대한 코드 이름을 추가할 수 있습니다. 각 코드를 해당 수신자에게 전송합니다.

   1. 개인 을 선택하면 왼쪽 아래에 새 탭인 쿠폰이 나타납니다. 로 이동합니다. **[!UICONTROL Coupons]** 탭을 클릭하고 **[!UICONTROL Add]**.
   1. 팝업 창에서 메시지가 표시되면 개별 쿠폰에 대한 고유 코드를 입력합니다.
   1. 클릭 **[!UICONTROL Save]** 쿠폰 생성.

   쿠폰 탭에 대한 자세한 내용은 [개별 쿠폰 구성](#configuring-individual-coupons).

   >[!NOTE]
   >
   >개별 쿠폰은 일괄적으로 가져올 수 있습니다. 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션](../../platform/using/get-started-data-import-export.md).

### 개별 쿠폰 구성 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

쿠폰 탭은 개별 쿠폰에서만 사용할 수 있습니다. 쿠폰이 게재와 연결되면 쿠폰 탭에서는 다음 세부 정보를 제공합니다.

* **[!UICONTROL Status]** : 쿠폰 사용 가능.
* **[!UICONTROL Redeemed on]** : 쿠폰이 상환된 날짜입니다.
* **[!UICONTROL Channel]** : 쿠폰을 보내는 데 사용된 채널입니다.
* **[!UICONTROL Address]** : 수신자의 이메일 주소입니다.

값 **[!UICONTROL status]**, **[!UICONTROL channel]**, 및 **[!UICONTROL address]** 자동으로 완료됩니다. 그러나 다음 값에 대한 **[!UICONTROL redeemed on]** Campaign에서 복구하지 않습니다. 쿠폰 상환에 대한 세부 정보가 있는 파일을 가져와서 완료할 수 있습니다.

## 이메일 게재에 쿠폰 삽입 {#inserting-a-coupon-into-an-email-delivery}

아래 예에서는 게재가 홈 페이지에서 만들어집니다. 게재를 만드는 방법에 대한 자세한 지침은 [이 섹션](about-email-channel.md). 워크플로우에서 게재에 쿠폰을 추가할 수도 있습니다.

1. 이동 **[!UICONTROL Campaigns]** 및 **[!UICONTROL Deliveries]**.
1. **[!UICONTROL Create]**&#x200B;를 클릭합니다.

   ![](assets/deliv_coup_04.png)

1. 이름을 입력합니다. **[!UICONTROL Label]** 을(를) 클릭합니다. **[!UICONTROL Continue]**.
1. 클릭 **[!UICONTROL To]** 수신자를 추가하려면
1. 클릭 **[!UICONTROL Add]** 을(를) 클릭하여 게재할 수신자를 선택합니다. 수신자를 선택하면 **[!UICONTROL Ok]** 게재로 돌아갑니다.

   ![](assets/deliv_coup_05.png)

1. 제목을 입력하고 메시지에 콘텐츠를 추가합니다.

   ![](assets/deliv_coup_06.png)

1. 도구 모음에서 **[!UICONTROL Properties]** 그리고 **[!UICONTROL Advanced]** 탭.
1. 폴더 아이콘 을 클릭합니다. **[!UICONTROL Coupon management]**.

   ![](assets/deliv_coup_07.png)

1. 쿠폰을 선택하고 **[!UICONTROL Ok]**. 클릭 **[!UICONTROL Ok]** 다시 한 번

   ![](assets/deliv_coup_08.png)

1. 메시지를 클릭하여 쿠폰을 배치할 위치를 선택합니다.

   ![](assets/deliv_coup_09.png)

1. 쿠폰 유형을 기준으로 다음 중 하나를 선택하려면 개인화 아이콘을 클릭합니다.

   * 익명 쿠폰: **[!UICONTROL Coupon > Coupon code]**

      ![](assets/deliv_coup_10.png)

   * 개별 쿠폰: **[!UICONTROL Coupon value > Coupon code]**

      ![](assets/deliv_coup_11.png)

      쿠폰은 지정한 이름이 아닌 코드로 메시지에 삽입됩니다. 이 코드는 Campaign otb 데이터 모델 내에서 사용됩니다.
   ![](assets/deliv_coup_12.png)

1. 테스트를 실행하여 쿠폰에 지정한 이름을 확인합니다. 로 이동합니다. **[!UICONTROL Preview]** 탭을 클릭하고 **[!UICONTROL Test personalization]**. 테스트할 수신자를 선택합니다.

   ![](assets/deliv_coup_13.png)

   테스트 후에는 쿠폰이 코드 대신 지정된 이름으로 표시되어야 합니다.

   ![](assets/deliv_coup_14.png)

1. 도구 모음에서 **[!UICONTROL Send]** (왼쪽 위)에서 게재를 보낼 방법을 선택합니다.

   ![](assets/deliv_coup_15.png)

1. **[!UICONTROL Analyze]**&#x200B;을(를) 클릭합니다. 분석 로그에서 모든 수신자에 대한 쿠폰이 충분한지 확인한 경우 를 클릭합니다 **[!UICONTROL Confirm delivery]** 전송하기 위해

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>게재에 필요한 쿠폰 부족 관리 방법에 대한 지침은 [쿠폰 부족 관리](#managing-insufficient-coupons)

게재가 성공했는지 확인하려면:

1. 이동 **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**.
1. 을(를) 클릭합니다. **[!UICONTROL Deliveries]** 탭.

   ![](assets/deliv_coup_17.png)

   상태는 **[!UICONTROL Finished]** 을 참조하십시오.

>[!NOTE]
>
>기본적으로 쿠폰 관리 모듈은 **nms:recipient** 테이블. [자세히 알아보기](../../configuration/using/about-data-model.md#default-recipient-table)
>
>사용자 지정 수신자 테이블을 사용하는 방법을 알아봅니다 [이 페이지에서](../../configuration/using/about-custom-recipient-table.md).

## 쿠폰 부족 관리 {#managing-insufficient-coupons}

메시지보다 쿠폰이 적은 경우 게재 분석이 중지됩니다. 이러한 경우 쿠폰을 더 많이 가져오거나 메시지 수를 제한할 수 있습니다. 메시지 수를 제한하려면 아래 지침을 따르십시오.

1. 전자 메일 게재 창으로 이동합니다.
1. **[!UICONTROL To]**&#x200B;를 클릭합니다.
1. in **[!UICONTROL Select target]**&#x200B;로 이동합니다. **[!UICONTROL Exclusions]** 탭.

   ![](assets/deliv_coup_18.png)

1. 제외 설정 섹션에서 **[!UICONTROL Edit]**.
1. 보낼 메시지 수를 입력합니다 **[!UICONTROL Limit delivery to...messages]** 을(를) 클릭합니다. **[!UICONTROL Ok]**. 게재를 보낼 수 있습니다.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>제한된 수의 쿠폰을 관리할 때 게재 워크플로우를 통해 기준에 따라 게재를 분할할 수 있습니다. 대상을 제한하지 않고 선택한 모집단으로 쿠폰을 보내려는 경우에는 좋은 옵션입니다.
