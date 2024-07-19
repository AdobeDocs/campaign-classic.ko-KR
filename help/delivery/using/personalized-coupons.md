---
product: campaign
title: 개인화된 쿠폰
description: 개인화된 쿠폰을 만들고 삽입하는 방법을 알아봅니다
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Personalization
role: User
exl-id: 182939bb-7aff-4667-bda9-c5d48be3b946
source-git-commit: 8e5a328bee7701adfedec6a533cc21b4ce548187
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 1%

---

# 개인화된 쿠폰{#personalized-coupons}

게재에 쿠폰을 추가하면 수신자에게 제품 및 서비스에 대한 향상된 가치를 제공할 수 있습니다. Campaign 쿠폰 모듈을 사용하여 예정된 마케팅 오퍼에 추가할 쿠폰 세트를 만들 수 있습니다. 게재를 만들 준비가 되면 해당 쿠폰을 할당합니다. 쿠폰은 선택 기간 동안 유효하므로 할당된 쿠폰은 해당 게재 메시지에 고유하게 연결됩니다. 또한 Campaign은 게재를 보내기 전에 메시지 수에 대한 쿠폰이 충분한지 확인합니다.

>[!AVAILABILITY]
>
>엔터프라이즈(FFDA) 배포의 컨텍스트에서는 Campaign v8에서 쿠폰 관리를 사용할 수 없습니다. 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/config/architecture/ffda/enterprise-deployment){target="_blank"}를 참조하세요.

쿠폰 관리는 설치해야 하는 패키지를 사용합니다. 쿠폰 관리 기능이 있는지 확인하려면 **[!UICONTROL Administration > Configuration > Package management > Installed packages.]**&#x200B;을(를) 확인하세요.

쿠폰 데이터는 CSV 및 XML 포맷을 사용하여 가져오고 내보낼 수 있습니다. [자세히 알아보기](../../platform/using/get-started-data-import-export.md).

## 쿠폰 만들기 {#creating-a-coupon}

쿠폰 관리 모듈은 쿠폰을 생성할 때 다음 두 가지 옵션을 제공합니다.

* **익명**: 선택한 수신자 또는 수신자 목록을 위한 일반 쿠폰입니다.
* **개인**: 선택한 수신자를 위한 개인화된 쿠폰입니다.

아래 절차를 수행하기 전에 만들려는 쿠폰 유형을 알고 있는지 확인하십시오.

1. 캠페인 트리에서 **[!UICONTROL Resources > Campaign management > Coupons]**(으)로 이동합니다.

   ![](assets/deliv_coup_01.png)

1. **[!UICONTROL New]** 버튼을 클릭합니다.
1. **[!UICONTROL Label]** 필드에 쿠폰 이름을 입력하십시오. **[!UICONTROL Coupon code]**&#x200B;에 고유 코드가 자동으로 입력되었습니다. 코드를 유지하거나 새 코드를 입력할 수 있습니다.

   ![](assets/deliv_coup_02.png)

1. 쿠폰의 유효 기간을 설정하려면 **[!UICONTROL Start date]** 및 **[!UICONTROL End date]**&#x200B;을(를) 선택하십시오.
1. **[!UICONTROL Coupon type]**&#x200B;에서 익명 또는 개인을 선택하십시오.

   **[!UICONTROL Anonymous coupons]** : 익명 쿠폰은 모든 받는 사람에게 동일합니다. **쿠폰 유형** 메뉴에서 익명이 선택되었는지 확인하고 **저장**&#x200B;을 클릭하여 쿠폰을 생성합니다.

   **[!UICONTROL Individual coupons]** : 추가 쿠폰 코드를 사용하여 개별 쿠폰을 추가로 개인화할 수 있습니다. 예를 들어 스포츠 장비 매장에서 판매할 수 있도록 개별 쿠폰이 생성됩니다. 하지만, 수령자 명단이 길고 하나의 스포츠에 대한 동일한 열정을 공유하지 않는다. 스포츠(예: 축구, 축구, 야구 등)에 따라 개별 쿠폰에 대한 코드 이름을 추가할 수 있습니다. 해당하는 수신자에게 각 코드를 전송합니다.

   1. 개인을 선택하면 새 탭인 쿠폰이 왼쪽 하단에 나타납니다. **[!UICONTROL Coupons]** 탭으로 이동하여 **[!UICONTROL Add]**&#x200B;을(를) 클릭합니다.
   1. 팝업 창에서 메시지가 표시되면 개별 쿠폰에 대한 고유 코드를 입력합니다.
   1. 쿠폰을 생성하려면 **[!UICONTROL Save]**&#x200B;을(를) 클릭하십시오.

   쿠폰 탭에 대한 자세한 내용은 [개별 쿠폰 구성](#configuring-individual-coupons)을 참조하십시오.

   >[!NOTE]
   >
   >개별 쿠폰은 일괄 수입이 가능합니다. 가져오기 및 내보내기에 대한 자세한 내용은 [이 섹션](../../platform/using/get-started-data-import-export.md)을 참조하세요.

### 개별 쿠폰 구성 {#configuring-individual-coupons}

![](assets/deliv_coup_03.png)

쿠폰 탭은 개별 쿠폰에서만 사용할 수 있습니다. 쿠폰이 게재와 연계되면 쿠폰 탭에서 다음 세부 정보를 확인할 수 있습니다.

* **[!UICONTROL Status]** : 쿠폰 사용 가능.
* **[!UICONTROL Redeemed on]** : 쿠폰을 상환한 날짜입니다.
* **[!UICONTROL Channel]** : 쿠폰을 보내는 데 사용되는 채널입니다.
* **[!UICONTROL Address]** : 받는 사람의 전자 메일 주소입니다.

**[!UICONTROL status]**, **[!UICONTROL channel]** 및 **[!UICONTROL address]**&#x200B;의 값이 자동으로 완료됩니다. 그러나 **[!UICONTROL redeemed on]**&#x200B;의 값은 Campaign에서 복구되지 않습니다. 쿠폰 상환에 대한 세부 사항이 있는 파일을 가져와서 완료할 수 있습니다.

## 이메일 게재에 쿠폰 삽입 {#inserting-a-coupon-into-an-email-delivery}

아래 예에서는 게재가 홈 페이지에서 생성됩니다. 게재를 만드는 방법에 대한 자세한 지침은 [이 섹션](about-email-channel.md)을 참조하세요. 워크플로우에서 게재에 쿠폰을 추가할 수도 있습니다.

1. **[!UICONTROL Campaigns]**(으)로 이동하여 **[!UICONTROL Deliveries]**&#x200B;을(를) 선택합니다.
1. **[!UICONTROL Create]**&#x200B;를 클릭합니다.

   ![](assets/deliv_coup_04.png)

1. **[!UICONTROL Label]**&#x200B;에 이름을 입력하고 **[!UICONTROL Continue]**&#x200B;을(를) 클릭합니다.
1. 수신자를 추가하려면 **[!UICONTROL To]**&#x200B;을(를) 클릭하십시오.
1. **[!UICONTROL Add]**&#x200B;을(를) 클릭하여 게재할 수신자를 선택합니다. 받는 사람을 선택한 후 **[!UICONTROL Ok]**&#x200B;을(를) 클릭하여 게재로 돌아갑니다.

   ![](assets/deliv_coup_05.png)

1. 제목을 입력하고 메시지에 내용을 추가하십시오.

   ![](assets/deliv_coup_06.png)

1. 도구 모음에서 **[!UICONTROL Properties]**&#x200B;을(를) 클릭하고 **[!UICONTROL Advanced]** 탭을 선택합니다.
1. **[!UICONTROL Coupon management]**&#x200B;의 폴더 아이콘을 클릭합니다.

   ![](assets/deliv_coup_07.png)

1. 쿠폰을 선택하고 **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다. **[!UICONTROL Ok]**&#x200B;을(를) 다시 클릭합니다.

   ![](assets/deliv_coup_08.png)

1. 메시지를 클릭하여 쿠폰을 놓을 위치를 선택합니다.

   ![](assets/deliv_coup_09.png)

1. 개인화 아이콘을 클릭하여 쿠폰 유형에 따라 다음 중 하나를 선택합니다.

   * 익명 쿠폰: **[!UICONTROL Coupon > Coupon code]**

     ![](assets/deliv_coup_10.png)

   * 개별 쿠폰: **[!UICONTROL Coupon value > Coupon code]**

     ![](assets/deliv_coup_11.png)

     쿠폰은 지정한 이름이 아닌 코드로 메시지에 삽입됩니다. 이 코드는 Campaign ootb 데이터 모델 내에서 사용됩니다.

   ![](assets/deliv_coup_12.png)

1. 테스트를 실행하여 쿠폰에 할당한 이름을 확인합니다. **[!UICONTROL Preview]** 탭으로 이동하여 **[!UICONTROL Test personalization]**&#x200B;을(를) 클릭합니다. 테스트 수신자를 선택합니다.

   ![](assets/deliv_coup_13.png)

   테스트에 따라 쿠폰이 코드가 아닌 지정된 이름으로 표시되어야 합니다.

   ![](assets/deliv_coup_14.png)

1. 도구 모음에서 **[!UICONTROL Send]**(왼쪽 상단)을 클릭하고 게재를 보낼 방법을 선택합니다.

   ![](assets/deliv_coup_15.png)

1. **[!UICONTROL Analyze]**&#x200B;을(를) 클릭합니다. 분석 로그에서 모든 받는 사람에 대한 쿠폰이 충분하다고 확인되면 **[!UICONTROL Confirm delivery]**&#x200B;을(를) 클릭하여 보내세요.

   ![](assets/deliv_coup_16.png)

>[!NOTE]
>
>배달 중 부족한 쿠폰을 관리하는 방법에 대한 지침은 [부족한 쿠폰 관리](#managing-insufficient-coupons)를 참조하세요.

게재가 성공했는지 확인하려면:

1. **[!UICONTROL Explorer > Resources > Campaign management > Coupons]**(으)로 이동합니다.
1. **[!UICONTROL Deliveries]** 탭을 클릭합니다.

   ![](assets/deliv_coup_17.png)

   상태가 성공적으로 배달될 수 있도록 **[!UICONTROL Finished]**(으)로 읽혀집니다.

>[!NOTE]
>
>기본적으로 쿠폰 관리 모듈은 **nms:recipient** 테이블을 사용합니다. [자세히 알아보기](../../configuration/using/about-data-model.md#default-recipient-table).
>
>이 페이지](../../configuration/using/about-custom-recipient-table.md)에서 사용자 지정 받는 사람 테이블 [을(를) 사용하는 방법을 알아보세요.

## 부족한 쿠폰 관리 {#managing-insufficient-coupons}

메시지보다 쿠폰이 적으면 게재 분석이 중지됩니다. 이러한 경우 더 많은 쿠폰을 가져오거나 메시지 수를 제한할 수 있습니다. 메시지 수를 제한하려면 아래 지침을 따르십시오.

1. 이메일 게재 창으로 이동합니다.
1. **[!UICONTROL To]**&#x200B;를 클릭합니다.
1. **[!UICONTROL Select target]**&#x200B;에서 **[!UICONTROL Exclusions]** 탭으로 이동합니다.

   ![](assets/deliv_coup_18.png)

1. 제외 설정 섹션에서 **[!UICONTROL Edit]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Limit delivery to...messages]**&#x200B;에 보낼 메시지 수를 입력하고 **[!UICONTROL Ok]**&#x200B;을(를) 클릭합니다. 게재를 보낼 수 있습니다.

   ![](assets/deliv_coup_19.png)

>[!NOTE]
>
>제한된 수의 쿠폰을 관리할 때 게재 워크플로우를 사용하여 기준에 따라 게재를 분할할 수 있습니다. 대상을 제한하지 않고 선택한 모집단에 쿠폰을 보내려는 경우 적합한 옵션입니다.
