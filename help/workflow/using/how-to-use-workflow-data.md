---
product: campaign
title: 워크플로우 데이터 사용 방법
description: 워크플로우 데이터 사용 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: 5354d608-2fea-45f9-a0aa-11c7e965ab04
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# 워크플로우 데이터 사용 방법{#how-to-use-workflow-data}



## 데이터베이스 업데이트 {#updating-the-database}

수집된 모든 데이터는 데이터베이스 또는 게재를 업데이트하는 데 사용할 수 있습니다. 예를 들어 메시지 콘텐츠 개인화 가능성을 보강할 수 있습니다(메시지에 계약 수 포함, 지난해 평균 장바구니 지정 등). 또는 세부 모집단 타겟팅(계약 공동 소유자에게 메시지 보내기, 온라인 서비스 우수 구독자 1,000명 타겟팅 등) 이 데이터를 내보내거나 목록에 보관할 수도 있습니다.

### 목록 및 직접 업데이트 {#lists-and-direct-updates}

두 가지 전용 활동을 사용하여 Adobe Campaign 데이터베이스 및 기존 목록의 데이터를 업데이트할 수 있습니다.

* 다음 **[!UICONTROL List update]** 활동을 사용하면 작업 테이블을 데이터 목록에 저장할 수 있습니다.

   기존 목록을 선택하거나 만들 수 있습니다. 이 경우 이름과 레코드 폴더가 계산됩니다.

   ![](assets/s_user_create_list.png)

   을(를) 참조하십시오 [목록 업데이트](list-update.md).

* 다음 **[!UICONTROL Update data]** 활동은 데이터베이스의 필드에 대한 대량 업데이트를 수행합니다.

   자세한 내용은 다음을 참조하십시오. [데이터 업데이트](update-data.md).

### 구독/구독 취소 관리 {#subscription-unsubscription-management}

워크플로우를 통해 정보 서비스에 수신자를 구독 및 구독 취소하는 방법에 대한 자세한 내용은 [구독 서비스](subscription-services.md).

## 워크플로우를 통해 보내기 {#sending-via-a-workflow}

### 게재 활동 {#delivery-activity}

게재 활동은에 자세히 설명되어 있습니다. [게재](delivery.md).

### 게재 강화 및 타겟팅 {#enriching-and-targeting-deliveries}

게재는 컨텐츠를 사용자 정의하기 위해 또는 대상 모집단 선택의 프레임워크 내에서 워크플로우의 데이터를 처리할 수 있습니다.

예를 들어 DM 게재 프레임워크 내에서 워크플로우에서 수행된 데이터 조작에서 얻은 추가 데이터를 추출 파일에 포함할 수 있습니다.

![](assets/s_advuser_add_data_postal_mail.png)

일반적인 개인화 필드 외에도 워크플로우 단계의 개인화 필드를 게재 콘텐츠에 추가할 수 있습니다. DM 게재 프레임워크 내에서 출력 파일의 이름을 정의하기 위해 워크플로우 활동에 정의된 추가 데이터를 아래 예와 같이 게재 마법사에서 유지하고 액세스할 수 있습니다.

![](assets/s_advuser_using_additional_data.png)

워크플로우 테이블에 포함된 데이터는 항상 로 구성되어 있는 이름으로 식별됩니다. **targetData** 링크를 클릭합니다. 자세한 내용은 다음을 참조하십시오. [Target 데이터](data-life-cycle.md#target-data).

이메일 게재 프레임워크 내에서 개인화 필드는 아래 예와 같이 타겟팅 워크플로우 단계에서 수행된 타겟 확장의 데이터를 사용할 수도 있습니다.

![](assets/s_advuser_add_data_email.png)

타깃팅 활동에 세그먼트 코드가 지정된 경우 워크플로우 테이블의 특정 열에 추가되고 개인화 필드와 함께 제공됩니다. 모든 개인화 필드를 표시하려면 **[!UICONTROL Target extension > Other...]** 개인화 버튼을 통해 액세스할 수 있는 링크입니다.

![](assets/s_advuser_segment_code_select.png)
