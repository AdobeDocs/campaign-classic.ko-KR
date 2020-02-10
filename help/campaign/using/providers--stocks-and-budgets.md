---
title: 제공업체, 주식 및 예산
seo-title: 제공업체, 주식 및 예산
description: 제공업체, 주식 및 예산
seo-description: null
page-status-flag: never-activated
uuid: 6caffaaf-a6a6-40e1-8b17-07c81748382c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: d4627141-cef1-4ddb-ad6a-5dc217b9fa96
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 제공업체, 주식 및 예산{#providers-stocks-and-budgets}

Adobe Campaign을 사용하면 캠페인 내에서 수행되는 작업에 관여할 서비스 공급자를 정의할 수 있습니다. 서비스 제공업체 및 관련 비용 구조에 대한 정보는 기본 보기에서 Adobe Campaign 관리자가 정의합니다. 서비스 제공업체는 납품에서 참조되며, 해당 비용 구조를 통해 이 게재와 관련된 비용 및 해당 주식의 관리를 계산할 수 있습니다.

## 서비스 제공업체 및 비용 구조 만들기 {#creating-service-providers-and-their-cost-structures}

각 서비스 제공업체는 연락처 정보, 서비스 템플릿 및 관련 작업이 있는 파일에 저장됩니다.

서비스 공급자는 트리의 **[!UICONTROL Administration > Campaign management]** 노드에 구성됩니다.

배달 중에 수행되는 작업은 서비스 제공 업체가, 특히 DM 및 모바일 채널에 대해 수행됩니다. 예를 들어 이러한 서비스 제공업체는 메시지를 인쇄하거나 배포하는 데 관여할 수 있습니다. 이러한 작업에는 각 서비스 제공업체에 적용되는 구성 및 비용이 포함됩니다. 서비스 제공업체의 구성은 4가지 단계로 이루어집니다.

1. Adobe Campaign에서 서비스 공급자 생성

   서비스 [공급자](#adding-a-service-provider)추가를 참조하십시오.

1. 관련 서비스 템플릿의 비용 범주 및 구조 정의

   원가 [범주](#defining-cost-categories) 정의 및 [원가 구조](#defining-the-cost-structure)정의를 참조하십시오.

1. 프로세스 구성

   서비스와 [관련된 프로세스 구성을](#configuring-processes-associated-with-a-service)참조하십시오.

1. 캠페인 수준에서 서비스 공급자 참조

   서비스와 [캠페인](#associating-a-service-with-a-campaign)연관을 참조하십시오.

### 서비스 공급자 및 해당 비용 범주 만들기 {#creating-a-service-provider-and-its-cost-categories}

#### 서비스 공급자 추가 {#adding-a-service-provider}

배송에 필요한 만큼 서비스 공급자를 생성할 수 있습니다. 서비스 공급자를 추가하는 절차는 다음과 같습니다.

1. 서비스 제공업체 목록을 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL New]**&#x200B;또는 서비스 제공업체 목록 위의 **[!UICONTROL New]** 단추를 클릭합니다.
1. 창의 아래 섹션에서 서비스 공급자의 이름과 연락처 세부 정보를 지정합니다.

   ![](assets/s_ncs_user_supplier_node_01.png)

1. 단추를 클릭하여 서비스 공급자를 목록에 추가합니다. **[!UICONTROL Save]**

#### 비용 범주 정의 {#defining-cost-categories}

서비스 템플릿을 각 서비스 제공자와 연결해야 합니다. 이러한 템플릿에서, 먼저 비용 카테고리와 필요한 경우 해당 주식을 식별해야 합니다. 그런 다음 비용 구조를 통해 각 범주에 대한 원가 계산 규칙을 생성해야 합니다.

>[!NOTE]
>
>자세한 내용은 비용 구조 [정의를 참조하십시오](#defining-the-cost-structure).

비용 카테고리는 배달 유형(이메일, DM 등)에 적합한 비용 세트가 포함된 개체입니다. 또는 작업에 사용할 수 있습니다. 비용 범주는 서비스 제공업체와 관련된 서비스 템플릿으로 그룹화됩니다. 각 서비스 공급업체는 하나 이상의 서비스 템플릿을 참조할 수 있습니다.

서비스 템플릿을 만들고 컨텐츠를 정의하려면 다음 단계를 적용합니다.

1. 서비스 공급자의 **[!UICONTROL Services]** 탭에서 **[!UICONTROL Add]** 단추를 클릭하고 서비스 템플릿의 이름을 지정합니다.

   ![](assets/s_ncs_user_supplier_node_create_template.png)

1. 각 프로세스 유형에 대한 비용 카테고리를 만듭니다(DM/이메일 등으로 전달). 또는 작업). 이렇게 하려면 **[!UICONTROL Cost categories]** 탭을 클릭한 다음 **[!UICONTROL Add]** 단추를 클릭하고 각 비용 범주의 매개변수를 입력합니다.

   ![](assets/s_ncs_user_supplier_node_03.png)

   * 이 원가 범주에 대한 레이블을 입력하고 관련 프로세스 유형을 선택합니다.전달 방법 **[!UICONTROL Direct mail]**, **[!UICONTROL E-mail]**, **[!UICONTROL Mobile]**&#x200B;또는 **[!UICONTROL Telephone]**&#x200B;그 **[!UICONTROL Fax]** 외의 방법에 **[!UICONTROL Task]**&#x200B;따라
   * 이 카테고리와 연관된 비용 유형을 정의하려면 **[!UICONTROL Add]** 단추를 클릭합니다.
   * 필요한 경우, 사용된 수량이 기존 주식과 자동으로 관련되도록 각 유형의 원가와 재고 라인을 연관시킵니다.

      >[!NOTE]
      >
      >스톡 라인은 **[!UICONTROL Stock management]** 노드에 정의됩니다.\
      >자세한 내용은 Stock 및 [주문 관리를](#stock-and-order-management)참조하십시오.

1. 이 비용 카테고리에 대한 값을 미리 선택할 수 있습니다. 이 비용 카테고리는 기본적으로 서비스 공급자 비용 카테고리(비어 있는 값 대신)에서 제공됩니다. 이렇게 하려면 해당 카테고리 유형에 대한 **[!UICONTROL Selected]** 열의 옵션을 선택합니다.

   ![](assets/s_ncs_user_supplier_cost_structure_defaut.png)

   배달 수준에서 기본적으로 값이 선택됩니다.

   ![](assets/s_ncs_user_supplier_default_cost.png)

### 원가 구조 정의 {#defining-the-cost-structure}

각 원가 유형에 대해 원가 구조는 적용할 계산 규칙을 지정합니다.

각 원가 범주 및 유형에 대한 원가 계산을 구성하려면 **[!UICONTROL Cost structure]** 탭을 클릭합니다. 비용 구조를 **[!UICONTROL Add]** 클릭하고 입력합니다.

![](assets/s_ncs_user_supplier_node_04.png)

* 원가 구조를 생성하려면 드롭다운 목록에서 메시지 유형 및 비용 범주 및 계산 규칙이 적용될 원가 유형을 선택합니다. 이러한 드롭다운 목록의 컨텐츠는 **[!UICONTROL Cost categories]** 탭을 통해 입력한 정보에서 가져옵니다.

   원가 구조에 레이블을 지정해야 합니다. 기본적으로 다음과 같은 배달 아웃라인이 있습니다.원가 **범주 - 원가**&#x200B;유형.

   그러나 이름을 변경할 수 있습니다.원하는 값을 **[!UICONTROL Label]** 필드에 직접 입력합니다.

* 원가 계산 공식은 창의 하단 섹션에 정의됩니다.

   이 공식은 메시지 수에 따라 수정하거나 계산할 수 있습니다.

   메시지 수에 따라 비용 계산 구조가 **[!UICONTROL Linear]**&#x200B;또는 **[!UICONTROL Linear by threshold]**&#x200B;또는 **[!UICONTROL Constant by threshold]**&#x200B;일 수 있습니다.

#### 선형 구조 {#linear-structure}

메시지(또는 메시지 일괄 처리)에 대한 금액이 총 메시지 수와 관계없이 항상 동일한 경우 각 메시지의 비용을 선택하고 **[!UICONTROL Linear]** 입력합니다.

![](assets/s_ncs_user_supplier_cost_structure_calc_01.png)

이 금액이 메시지 묶음에 적용되는 경우 **[!UICONTROL for]** 필드에 관련된 메시지 수를 지정합니다.

![](assets/s_ncs_user_supplier_cost_structure_calc_02.png)

#### 임계값에 따른 선형 구조 {#linear-structure-by-threshold}

각 메시지에 대해 임계값에 따라 금액이 적용되는 경우 **[!UICONTROL Linear by threshold]** 계산 구조를 정의해야 합니다. 이러한 유형의 비용 구조에서는 각 메시지의 총 메시지 수가 1에서 100 사이인 경우 0.13이 소요되며, 전송된 메시지 수 100개에서 1000개 사이 또는 메시지 수 0.11개가 초과됩니다.

구성은 다음과 같습니다.

![](assets/s_ncs_user_supplier_cost_structure_calc_03.png)

임계값을 추가하려면 목록 오른쪽에 있는 **[!UICONTROL Add]** 단추를 클릭합니다.

#### 임계값별 상수 구조 {#constant-structure-by-threshold}

마지막으로 총 메시지 수에 따라 비용 계산을 구성할 수 있습니다. 이렇게 하려면 **[!UICONTROL Constant by threshold]** 계산 구조를 선택합니다. 예를 들어 비용은 100-100 메시지의 경우 12.00, 메시지 101-1000개의 전달은 100.0, 메시지 1000개가 넘는 메시지의 경우 500.00으로 각각 설정됩니다.

![](assets/s_ncs_user_supplier_cost_structure_calc_04.png)

### 서비스와 연관된 프로세스 구성 {#configuring-processes-associated-with-a-service}

이 **[!UICONTROL Processes]** 탭을 통해 서비스와 관련된 프로세스에 대한 정보를 연결할 수 있습니다.

이렇게 하려면 **[!UICONTROL Processes]** 탭을 클릭하여 라우터에 정보 전송을 구성합니다.

![](assets/s_ncs_user_supplier_node_02.png)

* 이 **[!UICONTROL File extraction]** 섹션은 이 서비스를 선택할 때 배달에 사용되는 내보내기 템플릿을 나타냅니다. 필드에 출력 파일의 이름을 표시할 수 **[!UICONTROL Extraction file]** 있습니다. 필드 오른쪽의 단추를 사용하여 변수를 삽입할 수 있습니다.

   ![](assets/s_ncs_user_supplier_node_02a.png)

* 이 **[!UICONTROL Notification e-mail]** 섹션에서는 파일을 보낸 후 서비스 제공자에게 알릴 템플릿을 지정할 수 있습니다. 경고 메시지 및 수신자 그룹을 만드는 데 사용되는 템플릿을 선택합니다.

   기본적으로 알림 메시지에 대한 배달 템플릿은 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 노드에 저장되며, 이 노드는 일반 보기에서 액세스할 수 있습니다.

* 이 **[!UICONTROL Post-processing]** 섹션에서는 배달을 승인한 후 시작할 워크플로우를 선택할 수 있습니다. 워크플로우 템플릿을 입력하면 승인 작업이 진행되는 즉시 워크플로우 인스턴스가 자동으로 생성되어 실행됩니다. 이 워크플로우는 처리를 위해 추출 파일을 외부 서비스 제공자에게 보낼 수 있습니다.

### 서비스와 캠페인 연결 {#associating-a-service-with-a-campaign}

서비스는 배달 또는 작업을 통해 캠페인과 연결됩니다. 서비스 제공업체는 이 템플릿을 통해 생성된 배달에서 서비스를 제공하기 위해 배달 템플릿에 연결됩니다.

서비스를 선택하면 배달 유형(DM, 이메일 등)에 해당하는 비용 카테고리 는 정의된 처리 옵션과 함께 중앙 테이블에 자동으로 표시됩니다.

>[!NOTE]
>
>서비스를 선택할 때 비용 카테고리가 표시되지 않는 경우, 이 유형의 프로세스에 대해 정의된 비용 카테고리가 없음을 의미합니다. 예를 들어, 이메일 게재의 경우 **[!UICONTROL E-mail]** 유형 비용 카테고리가 정의되지 않은 경우 카테고리가 표시되지 않고 서비스를 선택해도 아무런 영향을 주지 않습니다.

* 직접 메일 배달을 위해 구성 창에서 서비스를 선택할 수 있습니다.

   ![](assets/s_ncs_user_supplier_mail_delivery_select.png)

* 모바일 채널, 팩스 또는 전화를 통한 전달의 경우 동일한 선택 모드가 적용됩니다.
* 이메일 전달의 경우 다음 예와 같이 배달 속성의 **[!UICONTROL Advanced]** 탭에서 서비스가 선택됩니다.

   ![](assets/s_ncs_user_supplier_email_delivery_select.png)

이 **[!UICONTROL Amount to surcharge]** 열을 사용하면 관련 배달 또는 작업의 컨텍스트에서 이 카테고리에 대한 비용을 추가할 수 있습니다.

납품에 대한 원가 범주 정의 중에 원가 유형을 필수 선택사항으로 지정할 수 있습니다. 이렇게 하려면 **[!UICONTROL A cost type must be selected]**&#x200B;선택합니다.

![](assets/s_ncs_user_supplier_cost_structure_select.png)

## 재고 및 주문 관리 {#stock-and-order-management}

경고, 공급 추적 및 주문 실행을 처리하기 위해 원가 유형을 재고 라인과 연결할 수 있습니다.

Adobe Campaign에서 스톡 및 주문 관리를 설정하고 배송에 대한 공급이 충분하지 않은 경우 운영자에게 알리는 절차는 다음과 같습니다.

1. 관련 서비스 제공업체의 스톡 제작 및 참조

   재고 [만들기를](#creating-a-stock)참조하십시오.

1. 재고 라인 추가

   재고 [라인](#adding-stock-lines)추가를 참조하십시오.

1. 경고 시 연산자 알림

   경고 [연산자를](#alerting-operators)참조하십시오.

1. 주문 및 공급.

   주문을 [참조하십시오](#orders).

### Stock 관리 {#stock-management}

Adobe Campaign은 재고가 부족하거나 최소 임계값에 도달한 경우 연산자 그룹에 경고를 줄 수 있습니다. 스톡 레벨은 탐색 영역의 **[!UICONTROL Stocks]** 링크를 통해 **[!UICONTROL Campaigns]** **[!UICONTROL Other choices]** 우주의 링크를 통해 액세스할 수 있습니다.

![](assets/s_ncs_user_stocks_view.png)

#### 스톡 만들기 {#creating-a-stock}

다음 단계를 적용하여 새 재고를 만듭니다.

1. 주식 목록 위의 **[!UICONTROL Create]** 단추를 클릭합니다.
1. 스톡 레이블을 입력하고 드롭다운 목록에서 스톡 레이블을 연결할 서비스 공급자를 선택합니다.

   ![](assets/s_ncs_user_stocks_add.png)

   >[!NOTE]
   >
   >자세한 내용은 서비스 제공업체 [및 비용 구조](#creating-service-providers-and-their-cost-structures)만들기를 참조하십시오.

#### 재고 라인 추가 {#adding-stock-lines}

주식은 다양한 주식들로 이루어져 있다. 재고 라인에는 납품에 의해 소비될 초기 자원 수량이 포함됩니다. 각 재고 라인은 소비 수량, 재고 수량 및 주문 수량을 나타냅니다.

스톡을 만들 때 **[!UICONTROL Stock lines]** 탭을 클릭하여 새 라인을 추가합니다.

![](assets/s_ncs_user_stocks_display_line.png)

스톡이 만들어지면 해당 대시보드를 클릭하여 편집하고 스톡 라인을 만들고 봅니다.

스톡 매개 변수를 정의하려면 **[!UICONTROL Create]** 단추를 클릭합니다.

![](assets/s_ncs_user_stocks_new_line.png)

* 처음에 **[!UICONTROL Initial stock]** 필드에서 재고 수량을 표시합니다. 캠페인이 진행되면 **[!UICONTROL Consumed]** 및 **[!UICONTROL In stock]** 필드가 자동으로 계산되고 업데이트됩니다.

   ![](assets/s_ncs_user_stocks_create_line.png)

* 필드에서 재고를 주문하기 위해 응답해야 하는 임계값을 **[!UICONTROL Alert level]** 지정합니다. 경고 수준에 도달하면 이 Stock을 사용하여 게재의 승인 창에 경고 메시지가 표시됩니다.

#### 재고 및 원가 범주 연관 {#associating-a-stock-with-cost-categories}

특정 서비스 공급자의 경우 다음과 같이 서비스 비용 범주 중 하나에서 스톡 라인을 참조할 수 있습니다.

![](assets/s_ncs_user_stocks_select_from_supplier.png)

### 스톡 추적 {#stock-tracking}

#### 경고 연산자 {#alerting-operators}

게재에서 참조된 재고가 부족할 때 경고가 표시됩니다. 예를 들어 추출 파일이 승인되면 다음 경고가 표시됩니다.

![](assets/s_ncs_user_stocks_valid_alert.png)

#### 주문 수 {#orders}

이 **[!UICONTROL Orders]** 하위 탭에서는 현재 주문을 보고 새 주문을 저장할 수 있습니다.

![](assets/s_ncs_user_stocks_edit_from_board.png)

주문을 저장하려면 타깃팅된 스톡 라인을 편집하고 **[!UICONTROL Add]** 버튼을 클릭한 다음 납품 일자 및 주문 수량을 지정합니다.

![](assets/s_ncs_user_stocks_node_06.png)

>[!NOTE]
>
>납품 일자에 도달하면 주문 스톡 라인이 자동으로 사라지고 **[!UICONTROL Volume on order]** 필드에 입력된 수량이 **[!UICONTROL Tracking]** 탭에 추가됩니다. 이 수량은 재고 볼륨에 자동으로 추가됩니다.

![](assets/s_ncs_user_stocks_node_08.png)

이 **[!UICONTROL Consumptions]** 탭에는 캠페인당 소비되는 볼륨이 포함되어 있습니다. 이 탭의 정보는 수행된 게재에 따라 자동으로 입력됩니다. 단추를 클릭하여 해당 캠페인을 엽니다. **[!UICONTROL Edit]**

![](assets/s_ncs_user_stocks_edit_from_board_consumed.png)

## 예산 계산 {#calculating-budgets}

### 원칙 {#principle}

비용은 게재 및 캠페인에 대해 관리됩니다. 진도에 따라, 이러한 비용은 예산에 할당된다.

캠페인에 대한 배달 비용은 캠페인 수준에서 통합되며 프로그램의 모든 캠페인 비용은 해당 캠페인과 연관된 프로그램으로 전달됩니다. 전용 보고서를 사용하면 전체 플랫폼 또는 각 플랜 및 프로그램에 대한 예산을 추적할 수 있습니다.

### 구현 {#implementation}

캠페인에서 예산을 선택할 때 초기 금액을 입력해야 합니다. 계산된 비용은 입력한 금액(비용, 예상, 예약, 약정)의 약정 수준에 따라 자동으로 업데이트됩니다. 금액 [계산을](../../campaign/using/controlling-costs.md#calculating-amounts)참조하십시오.

>[!NOTE]
>
>예산 생성 절차는 예산 [생성에서](../../campaign/using/controlling-costs.md#creating-a-budget)제공됩니다.

