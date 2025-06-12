---
product: campaign
title: 게재 설정 기본 정보
description: 특정 v7 게재 설정 살펴보기
feature: Channel Configuration
role: User
hide: true
hidefromtoc: true
exl-id: 66250817-f829-4b8b-92dd-2daa92a97fe0
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 12%

---

# 게재 설정 {#about-delivery-settings}

다음 설정은 Campaign Classic에만 적용됩니다. 다른 게재 설정은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html){target="_blank"}를 참조하세요.

## 게재 분석 {#delivery-analysis}

### 게재 분석 성능 개선 {#improving-delivery-analysis}

게재 준비 속도를 높이려면 분석을 시작하기 전에 **[!UICONTROL Prepare the delivery parts in the database]** 옵션을 확인할 수 있습니다.

이 옵션을 활성화하면 게재 준비가 데이터베이스 내에서 직접 수행되므로 분석을 상당히 가속화할 수 있습니다.

현재 이 옵션은 다음 조건이 충족될 때만 사용할 수 있습니다.

* 게재는 이메일이어야 합니다. 다른 채널은 현재 지원되지 않습니다.
* 중간 소싱 또는 외부 공정순서를 사용하지 말고 일괄 게재 공정순서 유형만 사용해야 합니다. **[!UICONTROL Delivery properties]**&#x200B;의 **[!UICONTROL General]** 탭에서 사용되는 라우팅을 확인할 수 있습니다.
* 외부 파일에서 가져온 모집단을 타깃팅할 수 없습니다. 단일 게재의 경우 **[!UICONTROL Email parameters]**&#x200B;에서 **[!UICONTROL To]** 링크를 클릭하고 **[!UICONTROL Defined in the database]** 옵션이 선택되어 있는지 확인하십시오. 워크플로우에서 사용되는 게재의 경우 **[!UICONTROL Delivery]** 탭에서 받는 사람이 **[!UICONTROL Specified by the inbound event(s)]**&#x200B;인지 확인하십시오.
* PostgreSQL 데이터베이스를 사용하고 있어야 합니다.

### 분석 우선 순위 구성 {#analysis-priority-}

게재가 캠페인의 일부인 경우 **[!UICONTROL Advanced]** 탭에서 추가 옵션을 제공합니다. 이렇게 하면 동일한 캠페인의 게재에 대한 처리 순서를 구성할 수 있습니다.

보내기 전에 각 게재를 분석합니다. 분석 기간은 게재 추출 파일에 따라 다릅니다. 파일 크기가 클수록 분석에 더 오래 걸려서 다음 게재가 대기하게 됩니다.

**[!UICONTROL Message preparation by the scheduler]**&#x200B;에 대한 옵션을 사용하면 캠페인 워크플로우에서 게재 분석의 우선 순위를 지정할 수 있습니다.

![](assets/delivery_analysis_priority.png)

게재가 너무 큰 경우 다른 워크플로우 게재 분석이 느려지지 않도록 우선 순위를 낮게 할당하는 것이 좋습니다.

>[!NOTE]
>
>더 큰 게재 분석으로 워크플로우의 진행 속도가 느려지지 않도록 **[!UICONTROL Schedule execution for a time of low activity]**&#x200B;을(를) 클릭하여 실행을 예약할 수 있습니다.

## 게재 전송 {#delivery-sending}

### 다시 시도 구성 {#configuring-retries}

**소프트** 또는 **무시됨** 오류로 인해 일시적으로 게재되지 않은 메시지는 자동 다시 시도될 수 있습니다. 게재 실패 유형 및 이유는 이 [섹션](understanding-delivery-failures.md#delivery-failure-types-and-reasons)에 나와 있습니다.

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 게재의 다시 시도 설정은 Campaign에서 더 이상 사용되지 않습니다. 소프트 바운스 재시도 및 재시도 간 시간은 메시지 이메일 도메인에서 돌아오는 바운스 응답의 유형 및 심각도에 따라 고급 MTA에 의해 결정됩니다.

이전 Campaign MTA를 사용하는 온-프레미스 설치 및 호스팅/하이브리드 설치의 경우 게재 매개 변수에 대한 **[!UICONTROL Delivery]** 탭의 중앙 섹션은 게재 다음 날에 수행해야 하는 다시 시도 횟수와 다시 시도 사이의 최소 지연을 나타냅니다.

![](assets/s_ncs_user_wizard_retry_param.png)

기본적으로 5번의 다시 시도가 배달 첫 날에 예약되며 하루 중 24시간 동안 최소 1시간 간격으로 분산됩니다. **[!UICONTROL Validity]** 탭에 정의된 배달 기한까지 하루에 한 번 다시 시도됩니다. [유효 기간 정의](#defining-validity-period)를 참조하십시오.

### 유효 기간 정의 {#defining-validity-period}

게재가 실행되면 게재 기한까지 메시지(및 다시 시도)를 보낼 수 있습니다. 게재 속성에는 **[!UICONTROL Validity]** 탭을 통해 표시됩니다.

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]** 필드를 사용하면 전역 게재 다시 시도에 대한 제한을 입력할 수 있습니다. 즉, Adobe Campaign은 시작 날짜부터 메시지를 전송하고 나서 메시지가 오류만 반환하는 경우 유효성 검사 제한에 도달할 때까지 구성 가능한 일반 재시도를 수행합니다.

  날짜를 지정할 수도 있습니다. 이렇게 하려면 **[!UICONTROL Explicitly set validity dates]**&#x200B;을(를) 선택합니다. 이 경우 게재 및 유효성 검사 제한 날짜를 통해 시간을 지정할 수도 있습니다. 기본적으로 현재 시간이 사용되지만 입력 필드에서 직접 수정할 수 있습니다.

  >[!IMPORTANT]
  >
  >호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](sending-with-enhanced-mta.md)(으)로 업그레이드한 경우 Campaign 이메일 게재의 **[!UICONTROL Delivery duration]** 설정은 **3.5일 이하**(으)로 설정된 경우에만 사용됩니다. 3.5일 이상의 값을 정의하면 고려되지 않습니다.

* **리소스의 유효성 제한**: **[!UICONTROL Validity limit]** 필드는 주로 미러 페이지와 이미지에 대해 업로드된 리소스에 사용됩니다. 이 페이지의 리소스는 제한된 시간 동안 유효합니다(디스크 공간을 절약하기 위함).

  이 필드의 값은 [이 섹션](../../platform/using/adobe-campaign-workspace.md#default-units)에 나열된 단위로 표현할 수 있습니다.
