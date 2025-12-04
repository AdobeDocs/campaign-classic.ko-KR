---
product: campaign
title: 격리 관리 이해
description: 격리 관리 이해
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---

# 격리 관리 이해{#understanding-quarantine-management}

>[!NOTE]
>
>격리 관리에 대한 포괄적인 지침은 [Campaign v8 격리 관리](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines) 페이지에 문서화되어 있습니다. 이 콘텐츠는 Campaign Classic v7 및 Campaign v8 사용자 모두에게 적용되며, 다음 내용을 다룹니다.
>
>* 차단 목록에 추가하다 방역 개념
>* 주소가 격리되는 이유(하드/소프트 오류)
>* 소프트 오류 관리 및 오류 카운터 임계값
>* 격리된 주소에 액세스하고 식별하는 방법
>* 격리에서 주소를 제거하는 방법 (자동, 수동, 벌크)
>* 격리 관리 보고서
>
>이 페이지는 하이브리드 및 온-프레미스 배포의 격리 관리를 위한 **Campaign Classic v7 관련 구성**&#x200B;을 문서화합니다.

포괄적인 격리 관리 지침은 [Campaign v8 격리 관리 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}를 참조하세요.

## 격리 구성 {#v7-quarantine-config}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;에서 격리 동작을 사용자 지정하는 데 다음 구성 옵션을 사용할 수 있습니다.

### 소프트 오류 임계값 구성 {#soft-error-threshold}

기존 Campaign MTA를 사용하는 온-프레미스 설치의 경우 주소가 격리되기 전에 오류 수와 두 오류 사이의 기간을 수정할 수 있습니다.

이러한 설정을 구성하려면 다음 작업을 수행하십시오.

1. **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Deployment wizard]**&#x200B;에서 배포 마법사에 액세스합니다.
2. **[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**(으)로 이동
3. Configure:
   * **오류 수**: 주소가 격리되기 전 최대 소프트 오류 수(기본값: 5)
   * **두 개의 중요한 오류 사이의 기간**: 오류 계산에 대한 시간 기간(초)(기본값: 86,400초 = 1일)

오류 카운터가 임계값에 도달하면 주소가 격리됩니다. 마지막으로 중요한 오류가 10일 이상 전에 발생한 경우 오류 카운터가 다시 초기화됩니다.

자세한 내용은 [게재 보내기](communication-channels.md) > **다시 시도 구성**&#x200B;에서 **이 페이지**&#x200B;를 참조하세요.

>[!NOTE]
>
>Campaign v8 관리 Cloud Services 사용자의 경우, 다시 시도 설정 및 오류 임계값은 IP 성능 및 도메인 평판에 따라 Adobe에서 관리합니다. 구성이 필요하지 않습니다.

### 데이터베이스 정리 워크플로 {#database-cleanup-workflow}

온-프레미스 설치의 경우 **[!UICONTROL Database cleanup]** 기술 워크플로우에서는 특정 조건과 일치하는 격리된 주소를 자동으로 제거합니다.

**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]** > **[!UICONTROL Database cleanup]**&#x200B;에서 이 워크플로에 액세스합니다.

워크플로우는 다음과 같은 경우 격리에서 주소를 제거합니다.

* 게재 성공 후 **[!UICONTROL With errors]** 상태의 주소
* 마지막 소프트 바운스가 10일 이상 전에 발생한 경우 **[!UICONTROL With errors]** 상태의 주소
* 30일 후 **[!UICONTROL With errors]** 오류가 발생한 **[!UICONTROL Mailbox full]** 상태의 주소

이 워크플로우가 격리 목록 위생 상태를 유지하기 위해 정기적으로(권장: 매일) 실행되는지 확인하십시오.

데이터베이스 정리에 대한 자세한 내용은 [이 섹션](../../production/using/database-cleanup-workflow.md)을 참조하세요.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 데이터베이스 정리 워크플로우는 Adobe에서 모니터링하고 관리합니다.

### 푸시 알림 격리 세부 정보 {#push-quarantine-specifics}

Campaign Classic v7의 경우 푸시 알림 격리는 일부 채널별 동작과 함께 일반적인 격리 메커니즘을 따릅니다.

**iOS** 및 **Android** 푸시 알림의 경우 격리 메커니즘에서 전자 메일 주소가 아닌 장치 토큰을 사용합니다. 모바일 애플리케이션을 제거하거나 다시 설치하면 연결된 토큰이 격리됩니다.

푸시 알림 격리 시나리오(iOS 및 Android 오류 유형, 다시 시도 동작 등)에 대한 자세한 내용은 포괄적인 푸시 알림 오류 유형 표를 포함하는 [게재 오류 이해](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} 설명서를 참조하십시오.

### SMS 격리 세부 정보 {#sms-quarantine-specifics}

Campaign Classic v7에서 SMS 격리는 전자 메일 주소가 아닌 전화번호와 관련된 일부 채널별 동작과 함께 일반적인 격리 메커니즘을 따릅니다.

SMS 격리 메커니즘은 사용되는 커넥터에 따라 다릅니다.

* **표준 SMPP 커넥터**: **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;에 정의된 오류 자격 규칙은 SMS 게재에 적용됩니다.

* **확장된 일반 SMPP 커넥터**: SMSC 공급자가 반환한 SR(상태 보고서) 메시지를 구문 분석하기 위해 오류 관리는 정규 표현식(정규 표현식)을 사용하여 다르게 처리됩니다.

SMS 격리 시나리오 및 오류 유형에 대한 자세한 내용은 포괄적인 SMS 오류 유형 표를 포함하는 [게재 오류 이해](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} 설명서를 참조하십시오.

## 관련 항목

* [격리 관리](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}(Campaign v8 설명서)
* [게재 실패 이해](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}(Campaign v8 설명서)
* [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}(Campaign v8 설명서)
* [데이터베이스 정리 워크플로우](../../production/using/database-cleanup-workflow.md)(v7 하이브리드/온-프레미스)
* [게재 다시 시도 구성](communication-channels.md)(v7 하이브리드/온-프레미스)
