---
product: campaign
title: 게재 실패 및 격리 관리
description: Campaign Classic v7에서 게재 실패를 이해하고 격리를 관리하는 방법을 알아봅니다
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 1%

---

# 게재 실패 및 격리 관리 {#delivery-failures-quarantine}

>[!NOTE]
>
>게재 실패 및 격리 관리에 대한 포괄적인 지침은 Campaign v8 설명서에 설명되어 있습니다. 이 콘텐츠는 Campaign Classic v7 및 Campaign v8 사용자 모두에게 적용됩니다.
>
>* [게재 오류 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} - 오류 유형, 오류 원인, 동기/비동기 오류, 관리 다시 시도 및 문제 해결
>* 차단 목록에 추가하다 [격리 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} - 격리 및 격리, 소프트 오류 임계값, 주소 제거 관련 정보를 제공합니다.
>
>이 페이지는 하이브리드 및 온-프레미스 배포의 바운스 메일 및 격리 관리를 위한 **Campaign Classic v7별 구성**&#x200B;을 문서화합니다.

## 게재 실패 이해

일반적인 게재 실패 개념, 오류 유형 및 문제 해결 지침은 [Campaign v8 게재 실패 이해 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}를 참조하세요.

## 바운스 메일 구성 {#bounce-mail-config}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;에서 바운스 메일 처리를 관리하는 데 다음 구성 옵션을 사용할 수 있습니다.

### 바운스 사서함 구성 {#bounce-mailbox-configuration}

온-프레미스 설치의 경우 바운스 사서함의 구성이 [이 섹션](../../installation/using/deploying-an-instance.md#managing-bounced-emails)에 자세히 설명되어 있습니다.

비동기 오류 메시지는 바운스 사서함을 통해 Adobe Campaign 플랫폼에서 수집되며 inMail 프로세스에서 정규화되어 전자 메일 관리 규칙 목록을 보강합니다.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 바운스 사서함 구성이 Adobe에서 수행되고 관리됩니다. 구성이 필요하지 않습니다.

### 반송 메일 조건 관리 {#bounce-mail-qualification-management}

기존 Campaign MTA를 사용하는 온-프레미스 설치 및 호스팅/하이브리드 설치의 경우 이메일 배달이 실패하면 Adobe Campaign 배달 서버가 메시징 서버 또는 원격 DNS 서버로부터 오류 메시지를 수신합니다. 오류 목록은 원격 서버에서 반환된 메시지에 포함된 문자열로 구성됩니다. 각 오류 메시지에는 실패 유형 및 이유가 지정됩니다.

이 목록은 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** 노드를 통해 사용할 수 있습니다. 여기에는 Adobe Campaign에서 게재 실패를 평가하는 데 사용하는 모든 규칙이 포함되어 있습니다. 완벽하지 않으며, Adobe Campaign에 의해 정기적으로 업데이트되며 사용자가 관리할 수도 있습니다.

![](assets/tech_quarant_rules_qualif.png)

이 오류 유형이 처음 발생할 때 원격 서버에서 반환된 메시지가 **[!UICONTROL First text]** 테이블의 **[!UICONTROL Delivery log qualification]** 열에 표시됩니다. 이 열이 표시되지 않으면 목록의 오른쪽 하단에 있는 **[!UICONTROL Configure list]** 단추를 클릭하여 선택하십시오.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign은 이 메시지를 필터링하여 변수 콘텐츠(예: ID, 날짜, 이메일 주소, 전화번호 등)를 삭제하고 필터링된 결과를 **[!UICONTROL Text]** 열에 표시합니다. 변수는 **`#xxx#`**(으)로 대체된 주소를 제외하고 **`*`**(으)로 대체됩니다.

이 프로세스를 통해 동일한 유형의 모든 오류를 종합하고 게재 로그 자격 표에서 유사한 오류에 대한 여러 항목을 방지할 수 있습니다.

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]** 필드에 목록의 메시지 발생 횟수가 표시됩니다. 발생 횟수는 100,000회로 제한됩니다. 예를 들어 필드를 재설정하려면 필드를 편집할 수 있습니다.

바운스 메일의 자격 상태는 다음과 같습니다.

* **[!UICONTROL To qualify]**: 바운스 메일을 정규화할 수 없습니다. 효율적인 플랫폼 전달성을 보장하기 위해 자격 조건을 전달성 팀에 할당해야 합니다. 자격이 없는 한 바운스 메일은 이메일 관리 규칙 목록을 보강하는 데 사용되지 않습니다.
* **[!UICONTROL Keep]**: 바운스 메일이 정규화되었으며 **배달 가능성을 위해 새로 고침** 워크플로우에서 기존 전자 메일 관리 규칙과 비교하여 목록을 보강하는 데 사용됩니다.
* **[!UICONTROL Ignore]**: Campaign MTA에서 바운스 메일을 무시합니다. 즉, 이 바운스로 인해 받는 사람의 주소가 격리되지 않습니다. **배달 가능성을 위해 새로 고침** 워크플로우에서 사용되지 않으며 클라이언트 인스턴스로 전송되지 않습니다.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>ISP가 중단되는 경우 Campaign을 통해 전송된 이메일이 바운스로 잘못 표시됩니다. 이 문제를 해결하려면 바운스 자격을 업데이트해야 합니다. 자세한 내용은 [이 페이지](update-bounce-qualification.md)를 참조하십시오.

### 이메일 관리 규칙 구성 {#email-management-rules}

메일 규칙은 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 노드를 통해 액세스됩니다. 전자 메일 관리 규칙은 창의 아래쪽에 표시됩니다.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>플랫폼의 기본 매개 변수는 배포 마법사에서 구성됩니다. 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md)을 참조하세요.

기본 규칙은 다음과 같습니다.

>[!IMPORTANT]
>
>* 매개변수가 변경된 경우 게재 서버(MTA)를 다시 시작해야 합니다.
>* 관리 규칙을 수정하거나 만드는 것은 전문가 사용자만을 위한 것입니다.

#### 인바운드 이메일 {#inbound-email}

이러한 규칙에는 원격 서버에서 반환할 수 있고 오류를 평가할 수 있는 문자열(**하드**, **소프트** 또는 **무시됨**)이 포함되어 있습니다.

이메일이 실패하면 원격 서버는 플랫폼 매개 변수에 지정된 주소로 바운스 메시지를 반환합니다. Adobe Campaign은 각 바운스 메시지의 콘텐츠를 규칙 목록의 문자열과 비교한 다음 세 가지 오류 유형 중 하나를 지정합니다.

>[!NOTE]
>
>사용자는 고유한 규칙을 만들 수 있습니다. 패키지를 가져올 때 및 **배달 가능성을 위해 새로 고침** 워크플로우를 통해 데이터를 업데이트할 때 사용자가 만든 규칙을 덮어씁니다.

바운스 메일 자격에 대한 자세한 정보는 [이 섹션](#bounce-mail-qualification-management)을 참조하세요.

#### 도메인 관리 {#domain-management}

온-프레미스 설치의 경우 MTA가 모든 도메인에 단일 **도메인 관리** 규칙을 적용합니다.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* **보낸 사람 ID**, **도메인 키**, **DKIM** 및 **S/MIME**&#x200B;과 같은 특정 ID 표준 및 암호화 키를 활성화할지 여부를 선택할 수 있습니다.
* **SMTP 릴레이** 매개 변수를 사용하면 특정 도메인에 대한 릴레이 서버의 IP 주소와 포트를 구성할 수 있습니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#smtp-relay)을 참조하십시오.

보낸 사람 주소에 메시지가 **[!UICONTROL on behalf of]**&#x200B;을(를) 표시하는 경우 Microsoft의 오래된 고유 전자 메일 인증 표준인 **보낸 사람 ID**&#x200B;로 전자 메일에 서명하지 않도록 합니다. **[!UICONTROL Sender ID]** 옵션이 활성화된 경우 해당 상자를 선택 취소하고 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오. 전달성은 영향을 받지 않습니다.

#### MX 관리 {#mx-management}

온-프레미스 설치의 경우 MX 관리 규칙을 사용하여 특정 도메인에 대한 발신 전자 메일의 흐름을 제어합니다.

<!--![](assets/tech_quarant_domain_rules_01.png)-->

이러한 규칙은 배포 마법사에서 사용할 수 있으며 사용자 지정할 수 있습니다.

* **[!UICONTROL MX Management]**: 이 규칙은 도메인의 발신 전자 메일 흐름을 제어하는 데 사용됩니다. 적절한 경우 바운스 메시지 및 전송 블록을 샘플링합니다.

* **[!UICONTROL Period]**: 메시지가 정체되거나 차단되는 기간.

* **[!UICONTROL Limit]**: 기간당 허용되는 최대 메시지 수입니다.

* **[!UICONTROL Type]**: 전송 동작을 확인하는 데 사용되는 오류 유형(하드, 소프트 또는 무시됨)입니다. 오류 유형 정의는 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}를 참조하세요.

MX 관리에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#about-mx-rules)을 참조하세요.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 MX 규칙 및 이메일 흐름 관리는 Adobe에서 관리 인프라의 일부로 관리됩니다. 특정 사용 사례에 맞게 MX 설정을 조정해야 하는 경우 Adobe 고객 지원 센터에 문의하십시오.

## 격리 관리 {#quarantine-management}

포괄적인 격리 관리 지침은 [Campaign v8 격리 관리 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}를 참조하세요.

## 격리 구성 {#quarantine-config}

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

푸시 알림 격리 시나리오(iOS 및 Android 오류 유형, 다시 시도 동작 등)에 대한 자세한 내용은 포괄적인 푸시 알림 오류 유형 표를 포함하는 [게재 오류 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} 설명서를 참조하십시오.

### SMS 격리 세부 정보 {#sms-quarantine-specifics}

Campaign Classic v7에서 SMS 격리는 전자 메일 주소가 아닌 전화번호와 관련된 일부 채널별 동작과 함께 일반적인 격리 메커니즘을 따릅니다.

SMS 격리 메커니즘은 사용되는 커넥터에 따라 다릅니다.

* **표준 SMPP 커넥터**: **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]**&#x200B;에 정의된 오류 자격 규칙은 SMS 게재에 적용됩니다.

* **확장된 일반 SMPP 커넥터**: SMSC 공급자가 반환한 SR(상태 보고서) 메시지를 구문 분석하기 위해 오류 관리는 정규 표현식(정규 표현식)을 사용하여 다르게 처리됩니다.

SMS 격리 시나리오 및 오류 유형에 대한 자세한 내용은 포괄적인 SMS 오류 유형 표를 포함하는 [게재 오류 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} 설명서를 참조하십시오.

## 관련 항목

* [게재 실패 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}(Campaign v8 설명서)
* [격리 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}(Campaign v8 설명서)
* [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}(Campaign v8 설명서)
* [게재 상태](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"}(Campaign v8 설명서)
* [데이터베이스 정리 워크플로우](../../production/using/database-cleanup-workflow.md)(v7 하이브리드/온-프레미스)
* [게재 다시 시도 구성](communication-channels.md)(v7 하이브리드/온-프레미스)
* [바운스 자격 업데이트](update-bounce-qualification.md)(v7 하이브리드/온-프레미스)
* [전자 메일 게재 기능 구성](../../installation/using/email-deliverability.md)(v7 하이브리드/온-프레미스)
* [인스턴스 배포](../../installation/using/deploying-an-instance.md#managing-bounced-emails)(v7 하이브리드/온-프레미스)

