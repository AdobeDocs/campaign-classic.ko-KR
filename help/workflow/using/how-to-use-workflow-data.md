---
solution: Campaign Classic
product: campaign
title: 워크플로우 데이터 사용 방법
description: 워크플로우 데이터 사용 방법 학습
audience: workflow
content-type: reference
topic-tags: -general-operation
translation-type: tm+mt
source-git-commit: 1901db70fde2b7b3c2789154bd93160012cd4c29
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

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
