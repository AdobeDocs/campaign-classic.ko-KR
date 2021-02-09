---
solution: Campaign Classic
product: campaign
title: 게재 실패 이해
description: 전달 실패를 이해하는 방법 살펴보기
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 72fdac4afba6c786cfbd31f4a916b0539ad833e3
workflow-type: tm+mt
source-wordcount: '2572'
ht-degree: 14%

---


# 게재 실패 이해{#understanding-delivery-failures}

## 게재 실패 기본 정보{#about-delivery-failures}

메시지(이메일, SMS, 푸시 알림)를 프로필에 보낼 수 없는 경우 원격 서버는 오류 메시지를 자동으로 전송합니다. 오류 메시지는 Adobe Campaign 플랫폼에 의해 선택되었고 이메일 주소 또는 전화 번호를 격리해야 하는지 여부를 결정할 수 있는 자격이 있습니다. [바운스 메일 관리](#bounce-mail-management)를 참조하십시오.

>[!NOTE]
>
>**이메일** 오류 메시지(또는 &quot;반송&quot;)는 Enhanced MTA(동기 반송) 또는 inMail 프로세스(비동기 반송)에 의해 검증됩니다.
>
>**SMS** 오류 메시지(또는 &quot;상태 보고서&quot;의 경우 &quot;SR&quot;)는 MTA 프로세스에 의해 검증됩니다.

메시지가 전송되면 배달 로그를 사용하여 각 프로필에 대한 배달 상태, 연관된 실패 유형 및 이유를 볼 수 있습니다.

주소가 격리되거나 프로파일이에 있는 경우에도 전달 준비 중에 메시지를 제외할 수 차단 목록 있습니다. 제외된 메시지는 배달 대시보드에 나열됩니다.

**관련 항목:**

* [배달 로그 및 내역](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)
* [실패 상태](../../delivery/using/delivery-performances.md#failed-status)
* [게재 실패 유형 및 이유](#delivery-failure-types-and-reasons)

## 게재 실패 유형 및 이유 {#delivery-failure-types-and-reasons}

메시지가 실패하면 3가지 유형의 오류가 있습니다. 각 오류 유형은 검역소에 주소를 보내는지 여부를 결정합니다. 이에 대한 자세한 내용은 [격리](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)로 주소를 전송하는 조건을 참조하십시오.

* **하드**: &quot;하드&quot; 오류는 잘못된 주소를 나타냅니다. 여기에는 &quot;알 수 없는 사용자&quot;와 같이 주소가 유효하지 않다는 오류 메시지가 명시적으로 표시됩니다.
* **소프트**: 일시적인 오류이거나 &quot;잘못된 도메인&quot; 또는 &quot;사서함 가득 참&quot;과 같이 분류할 수 없는 오류일 수 있습니다.
* **무시됨**: &quot;부재 중&quot;과 같이 일시적인 것으로 알려진 오류이거나 예를 들어 발신자 유형이 &quot;postmaster&quot;인 경우와 같이 기술적인 오류입니다.

게재 실패 이유는 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td> 오류 레이블 </td> 
   <td> 오류 유형 </td> 
   <td> 기술 가치 </td> 
   <td> 설명 </td> 
  </tr> 
  <tr> 
   <td> 계정이 비활성화됨 </td> 
   <td> 소프트/하드 </td> 
   <td> 4 </td> 
   <td> 주소에 연결된 계정이 더 이상 활성화되지 않습니다. IAP(Internet Access Provider)에서 장기간 동안 사용되지 않는 기간을 감지하면 사용자의 계정을 닫을 수 있습니다. 그러면 사용자 주소로 배달할 수 없습니다. 6개월 동안 활동이 없어 계정을 일시적으로 사용할 수 없고 계속 활성화할 수 있는 경우 오류 시 상태가 할당되고 오류 카운터가 5에 도달할 때까지 계정이 다시 시도됩니다. 오류가 해당 계정이 영구적으로 비활성화되었음을 알리는 메시지가 표시되면 즉시 격리 상태로 설정됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 격리 주소 </td> 
   <td> 하드 </td> 
   <td> 9 </td> 
   <td> 주소가 격리되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 주소가 지정되지 않음 </td> 
   <td> 하드 </td> 
   <td> 7 </td> 
   <td> 받는 사람에 대한 주소가 지정되지 않았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 고품질 주소 </td> 
   <td> 무시됨 </td> 
   <td> 14 </td> 
   <td> 이 주소의 품질 등급이 너무 낮습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 차단 목록에 추가된 주소 </td> 
   <td> 하드 </td> 
   <td> 8 </td> 
   <td> 주소를 차단 목록 보낼 때에 추가되었습니다. 이 상태는 외부 목록 및 외부 시스템의 데이터를 Adobe Campaign 격리 목록으로 가져오는 데 사용됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 제어 주소 </td> 
   <td> 무시됨 </td> 
   <td> 127년 </td> 
   <td> 받는 사람의 주소는 제어 그룹의 일부입니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> Double </td> 
   <td> 무시됨 </td> 
   <td> 10 </td> 
   <td> 받는 사람의 주소가 이 배달에 이미 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 오류가 무시됨 </td> 
   <td> 무시됨 </td> 
   <td> 25 </td> 
   <td> 주소는에 허용 목록에 추가하다 있습니다. 따라서 오류가 무시되고 전자 메일이 전송됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 중재 후 제외 </td> 
   <td> 무시됨 </td> 
   <td> 12 </td> 
   <td> 받는 사람이 '중재' 유형 캠페인 유형 규칙에 의해 제외되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQL 규칙으로 제외 </td> 
   <td> 무시됨 </td> 
   <td> 11 </td> 
   <td> 수신자가 'SQL' 유형 캠페인 유형 규칙에 의해 제외되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 잘못된 도메인 </td> 
   <td> 소프트 </td> 
   <td> 2 </td> 
   <td> 이메일 주소의 도메인이 잘못되었거나 더 이상 존재하지 않습니다. 이 프로필은 오류 수가 5개에 도달할 때까지 다시 타겟팅됩니다. 이후 레코드가 격리 상태로 설정되며 다시 시도되지 않습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 사서함 전체 </td> 
   <td> 소프트 </td> 
   <td> 5 </td> 
   <td> 이 사용자의 사서함이 가득 찼으므로 더 많은 메시지를 받을 수 없습니다. 이 프로필은 오류 수가 5개에 도달할 때까지 다시 타겟팅됩니다. 이후 레코드가 격리 상태로 설정되며 다시 시도되지 않습니다.<br /> 이 유형의 오류는 정리 프로세스에 의해 관리되며 30일 후 주소가 유효한 상태로 설정됩니다.<br /> 경고:격리된 주소 목록에서 주소를 자동으로 제거하려면 데이터베이스 정리 기술 작업 과정을 시작해야 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 연결되지 않음 </td> 
   <td> 무시됨 </td> 
   <td> 6 </td> 
   <td> 메시지를 보낼 때 받는 사람의 휴대 전화가 꺼져 있거나 네트워크에 연결되지 않았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 정의되지 않음 </td> 
   <td> 정의되지 않음 </td> 
   <td> 0 </td> 
   <td> 오류가 아직 증가하지 않았기 때문에 주소가 적격 상태입니다. 이 유형의 오류는 서버에서 새 오류 메시지를 보낼 때 발생합니다. 이는 격리된 오류일 수 있지만 다시 발생하면 오류 카운터가 증가하여 기술 팀에게 알립니다. 그런 다음 트리 구조의 <span class="uicontrol">관리</span> / <span class="uicontrol">캠페인 관리</span> / <span class="uicontrol">비결과물 관리</span> 노드를 통해 메시지 분석을 수행하고 이 오류를 평가할 수 있습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 오퍼에 가입할 수 없음 </td> 
   <td> 무시됨 </td> 
   <td> 16 </td> 
   <td> 받는 사람이 배달에서 오퍼에 참여할 수 없습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 거부됨 </td> 
   <td> 소프트/하드 </td> 
   <td> 20년 </td> 
   <td> 스팸성 보고서로 보안 피드백이 발생하여 주소가 격리되었습니다. 오류에 따르면, 오류 카운터가 5에 도달하거나 검역소에 직접 보내질 때까지 주소가 다시 시도됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 크기가 제한된 Target </td> 
   <td> 무시됨 </td> 
   <td> 17 </td> 
   <td> 받는 사람의 최대 배달 크기에 도달했습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 비인가 주소 </td> 
   <td> 무시됨 </td> 
   <td> 15 </td> 
   <td> 우편 주소가 적격하지 않았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 연결할 수 없습니다. </td> 
   <td> 소프트/하드 </td> 
   <td> 3 </td> 
   <td> 메시지 배달 체인에 오류가 발생했습니다. SMTP 중계기, 일시적으로 연결할 수 없는 도메인 등에 발생한 사고일 수 있습니다. 오류에 따르면, 오류 카운터가 5에 도달하거나 검역소에 직접 보내질 때까지 주소가 다시 시도됩니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 알 수 없음 </td> 
   <td> 하드 </td> 
   <td> 1 </td> 
   <td> 주소가 없습니다. 이 프로필에 대해 더 이상 게재를 시도하지 않습니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 일시적 게재 실패 후 다시 시도 {#retries-after-a-delivery-temporary-failure}

**Soft** 또는 **Ignored** 오류로 인해 메시지가 실패한 경우 배달 기간 동안 재시도가 수행됩니다.

>[!NOTE]
>
>일시적으로 배달되지 않은 메시지는 **소프트** 또는 **무시된** 오류와 관련될 수 있지만 **하드** 오류가 아닙니다([배달 실패 유형 및 이유](#delivery-failure-types-and-reasons) 참조).

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드한 경우, 게재의 재시도 설정은 더 이상 Campaign에서 사용되지 않습니다. 소프트 바운스 재시도 횟수와 그 사이의 시간은 메시지의 이메일 도메인에서 돌아오는 바운스 응답 유형 및 심각도에 따라 향상된 MTA에 의해 결정됩니다.

기존 캠페인 MTA를 사용하여 온-프레미스 설치 및 호스팅된/하이브리드 설치의 경우 배달 기간을 수정하려면 전달 또는 배달 템플릿의 고급 매개 변수로 이동하고 해당 필드에 원하는 기간을 지정합니다. [유효성 기간 정의](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)를 참조하십시오.

기본 구성을 사용하면 1시간 간격으로 5회 재시도 후 4일 동안 1회 재시도 재시도 횟수는 전역적으로(Adobe 기술 관리자에게 문의) 또는 각 배달 또는 배달 템플릿에 대해 변경할 수 있습니다([재시도 구성](../../delivery/using/steps-sending-the-delivery.md#configuring-retries) 참조).

## 동기 및 비동기 오류 {#synchronous-and-asynchronous-errors}

메시지는 전송(비동기 오류)한 후 즉시 실패하거나 나중에 실패할 수 있습니다(비동기 오류).

* 동기 오류:adobe campaign 배달 서버가 연결한 원격 메일 서버에서 오류 메시지를 바로 반환했습니다. 전달을 프로필의 서버로 보낼 수 없습니다. Adobe Campaign은 해당 이메일 주소를 격리할지 여부를 결정하기 위해 각 오류를 확인합니다. [반송 메일 조건](#bounce-mail-qualification)을 참조하십시오.
* 비동기 오류: 반송 메일 또는 SR이 나중에 수신 서버에 의해 다시 전송되었습니다. 이 메일은 응용 프로그램에서 오류 메시지를 레이블에 지정하는 데 사용하는 기술 사서함에 로드됩니다. 게재를 보낸 후 1주일까지 비동기 오류가 발생할 수 있습니다.

   >[!NOTE]
   >
   >바운스 사서함의 구성은 [이 섹션](../../installation/using/deploying-an-instance.md#managing-bounced-emails)에 자세히 설명되어 있습니다.

   [피드백 루프](../../delivery/using/technical-recommendations.md#feedback-loop)는 바운스 이메일과 같이 작동합니다. 사용자가 이메일을 스팸으로 취급하면 Adobe Campaign에서 이메일 규칙을 구성하여 이 사용자에 대한 모든 배달을 차단할 수 있습니다. 스팸으로 이메일을 자격을 부여받은 사용자에게 보낸 메시지는 이러한 목적으로 특별히 작성된 이메일 상자로 자동으로 리디렉션됩니다. 이러한 사용자의 주소는 구독 취소 링크를 클릭하지 차단 목록 않아도에 있습니다. 주소는 (**NmsAddress**) 격리 테이블에 있고 (**NmsRecipient**) 수신자 테이블에 차단 목록 없습니다.

   >[!NOTE]
   >
   >불만 관리는 [배달 가능성 관리](../../delivery/using/about-deliverability.md) 섹션에 자세히 설명되어 있습니다.

## 바운스 메일 관리 {#bounce-mail-management}

Adobe Campaign 플랫폼을 사용하면 바운스 메일 기능을 통해 이메일 배달 오류를 관리할 수 있습니다.

전자 메일을 받는 사람에게 배달할 수 없는 경우 원격 메시징 서버는 이 용도로 디자인된 기술 받은 편지함에 오류 메시지(바운스 메일)를 자동으로 반환합니다.

기존 캠페인 MTA를 사용하는 온-프레미스 설치 및 호스팅된/하이브리드 설치의 경우, 오류 메시지는 Adobe Campaign 플랫폼에 의해 수집되고 inMail 프로세스를 통해 이메일 관리 규칙 목록을 보완합니다.

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드한 경우 대부분의 이메일 관리 규칙이 더 이상 사용되지 않습니다. 자세한 내용은 [이 섹션](#email-management-rules)을 참조하십시오.

### 반송 메일 조건 {#bounce-mail-qualification}

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드한 경우:
>
>* **[!UICONTROL Delivery log qualification]** 테이블의 바운스 자격 조건은 더 이상 **동기** 배달 실패 오류 메시지에 사용되지 않습니다. 향상된 MTA는 바운스 유형 및 자격을 결정하고 해당 정보를 Campaign에 다시 전송합니다.
   >
   >
* ****&#x200B;비동기 반송은 **[!UICONTROL Inbound email]** 규칙을 통해 inMail 프로세스에 의해 계속 검증됩니다. 자세한 내용은 [이메일 관리 규칙](#email-management-rules)을 참조하십시오.
   >
   >
* Webhook/EFS **없이 향상된 MTA**&#x200B;을 사용하는 인스턴스의 경우 비동기 바운스 이메일과 동일한 이메일 주소를 사용하여 향상된 MTA에서 들어오는 동기 바운스 이메일을 처리하는 데도 **[!UICONTROL Inbound email]** 규칙이 사용됩니다.


기존 캠페인 MTA를 사용하는 온-프레미스 설치 및 호스팅된/하이브리드 설치의 경우, 이메일 배달이 실패하면 Adobe Campaign 게재 서버는 메시징 서버 또는 원격 DNS 서버로부터 오류 메시지를 수신합니다. 오류 목록은 원격 서버에서 반환된 메시지에 포함된 문자열로 구성됩니다. 각 오류 메시지에 오류 유형 및 이유를 지정합니다.

이 목록은 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** 노드를 통해 사용할 수 있습니다. 여기에는 Adobe Campaign에서 배달 실패를 평가하는 데 사용하는 모든 규칙이 포함됩니다. 비배타적, 그리고 Adobe Campaign에 의해 정기적으로 업데이트되며 사용자가 관리할 수도 있습니다.

![](assets/tech_quarant_rules_qualif.png)

이 오류 유형의 첫 번째 발생 시 원격 서버에서 반환된 메시지는 **[!UICONTROL Delivery log qualification]** 테이블의 **[!UICONTROL First text]** 열에 표시됩니다. 이 열이 표시되지 않으면 목록 오른쪽 하단에 있는 **[!UICONTROL Configure list]** 단추를 클릭하여 선택합니다.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign은 이 메시지를 필터링하여 변수 컨텐츠(예: ID, 날짜, 이메일 주소, 전화 번호 등)를 삭제합니다. 그리고 필터링된 결과를 **[!UICONTROL Text]** 열에 표시합니다. 변수는 **`*`**&#x200B;로 바뀐 주소를 제외하고 **`#xxx#`**&#x200B;으로 바뀝니다.

이 프로세스를 통해 동일한 유형의 모든 오류를 취합하고 배달 로그 자격 표의 유사한 오류에 대한 여러 항목을 방지할 수 있습니다.

>[!NOTE]
>
>**[!UICONTROL Number of occurrences]** 필드에는 목록에 있는 메시지 발생 횟수가 표시됩니다. 100 0,000개로 제한됩니다. 예를 들어 원하는 경우 필드를 편집하여 재설정할 수 있습니다.

바운스 메일의 자격 상태는 다음과 같습니다.

* **[!UICONTROL To qualify]** :바운스 메일을 적격화할 수 없습니다. 효율적인 플랫폼 제공을 보장하려면 제공 팀에 자격 조건을 할당해야 합니다. 자격이 없는 경우 바운스 메일은 이메일 관리 규칙 목록을 채우는 데 사용되지 않습니다.
* **[!UICONTROL Keep]** :바운스 메일은 자격을 얻었으며 기존 이메일 관리 규칙과 비교할  **수** 있는 전달 능력 새로 고침 워크플로에서 사용할 것입니다.
* **[!UICONTROL Ignore]** :바운스 메일은 캠페인 MTA에서 무시됩니다. 즉, 이 바운스는 받는 사람의 주소를 격리하지 않습니다. 배달 가능&#x200B;**작업 과정에 대해**&#x200B;새로 고침에서 사용하지 않으며 클라이언트 인스턴스로 전송되지 않습니다.

![](assets/deliverability_qualif_status.png)

### 이메일 관리 규칙 {#email-management-rules}

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드한 경우 대부분의 이메일 관리 규칙이 더 이상 사용되지 않습니다. 자세한 내용은 아래 섹션을 참조하십시오.

메일 규칙은 **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** 노드를 통해 액세스합니다. 창 아래쪽에 이메일 관리 규칙이 표시됩니다.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>플랫폼의 기본 매개 변수가 배포 마법사에 구성됩니다. 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md)을 참조하십시오.

기본 규칙은 다음과 같습니다.

>[!IMPORTANT]
>
>* 매개 변수가 변경된 경우 배달 서버(MTA)를 다시 시작해야 합니다.
>* 관리 규칙을 수정하거나 만드는 것은 전문가 사용자에게만 해당됩니다.


#### 인바운드 이메일 {#inbound-email}

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우, [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드했고 인스턴스에 **Webhook/EFS** 기능이 있는 경우 **[!UICONTROL Inbound email]** 규칙은 동기 배달 실패 오류 메시지에 더 이상 사용되지 않습니다. 자세한 내용은 [이 섹션](#bounce-mail-qualification)을 참조하십시오.

기존 캠페인 MTA를 사용하는 온-프레미스 설치 및 호스팅된/하이브리드 설치의 경우, 이러한 규칙에는 원격 서버에서 반환할 수 있는 문자 문자열 목록이 들어 있으며, 이를 통해 오류를 평가할 수 있습니다(**하드**, **소프트** 또는 **무시됨**).

이메일이 실패하면 원격 서버는 플랫폼 매개 변수에 지정된 주소로 바운스 메시지를 반환합니다. Adobe Campaign은 각 바운스 메일의 내용을 규칙 목록의 문자열에 있는 내용과 비교하고 3가지 [오류 유형 중 하나를 할당합니다](#delivery-failure-types-and-reasons).

>[!NOTE]
>
>사용자는 자신의 규칙을 만들 수 있습니다. 패키지를 가져오고 **배달 가능** 작업 과정을 위해 새로 고침을 통해 데이터를 업데이트할 때 사용자가 만든 규칙을 덮어씁니다.

바운스 메일 자격에 대한 자세한 내용은 [이 섹션](#bounce-mail-qualification)을 참조하십시오.

#### 도메인 관리 {#domain-management}

>[!IMPORTANT]
>
>호스팅되거나 하이브리드 설치의 경우 [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드한 경우 **[!UICONTROL Domain management]** 규칙은 더 이상 사용되지 않습니다. **DKIM(DomainKeys Identified Mail)** 전자 메일 인증 서명은 모든 도메인이 있는 모든 메시지에 대해 Enhanced MTA에서 수행합니다. Enhanced MTA 수준에서 별도로 지정하지 않는 한 **발신자 ID**, **도메인 키** 또는 **S/MIME**&#x200B;으로 서명하지않습니다.

기존 캠페인 MTA를 사용하는 온-프레미스 설치 및 호스트/하이브리드 설치의 경우 Adobe Campaign 메시징 서버는 모든 도메인에 단일 **도메인 관리** 규칙을 적용합니다.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* **보낸 사람 ID**, **도메인 키**, **DKIM** 및 **S/MIME**&#x200B;과 같은 특정 식별 표준 및 암호화 키를 활성화할지 여부를 선택할 수 있습니다.
* **SMTP 릴레이** 매개 변수를 사용하여 특정 도메인에 대한 IP 주소와 릴레이 서버의 포트를 구성할 수 있습니다. 자세한 내용은 [이 섹션](../../installation/using/configuring-campaign-server.md#smtp-relay)을 참조하십시오.

보낸 사람 주소에 **[!UICONTROL on behalf of]**&#x200B;이(가) 있는 Outlook에 메시지가 표시되는 경우, Microsoft의 구식 전자 메일 인증 표준인 **보낸 사람 ID**&#x200B;로 전자 메일을 서명하지 않았는지 확인하십시오. **[!UICONTROL Sender ID]** 옵션이 활성화되어 있으면 해당 상자의 선택을 취소하고 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오. 배달은 영향을 받지 않습니다.

#### MX 관리 {#mx-management}

>[!IMPORTANT]
>
>호스팅 또는 하이브리드 설치의 경우 [향상된 MTA](../../delivery/using/sending-with-enhanced-mta.md)로 업그레이드한 경우 **[!UICONTROL MX management]** 배달 처리량 규칙은 더 이상 사용되지 않습니다. 향상된 MTA는 고유한 MX 규칙을 사용하여 고유한 내역 이메일 명성을 기반으로 그리고 이메일을 보내는 도메인에서 오는 실시간 피드백을 바탕으로 처리량을 도메인별로 사용자 정의할 수 있습니다.

기존 캠페인 MTA를 사용하는 온-프레미스 설치 및 호스트/하이브리드 설치의 경우:

* MX 관리 규칙은 특정 도메인에 대한 나가는 이메일의 흐름을 제어하는 데 사용됩니다. 바운스 메시지를 샘플링하고 적절한 경우 전송을 차단합니다.

* Adobe Campaign 메시징 서버는 도메인과 관련된 규칙을 적용한 다음 규칙 목록에서 별표로 표시되는 일반 사례에 대한 규칙을 적용합니다.

* MX 관리 규칙을 구성하려면 임계값을 설정하고 특정 SMTP 매개 변수를 선택하면 됩니다. **임계값**&#x200B;은 특정 도메인에 대한 모든 메시지가 차단되는 오류 백분율로 계산되는 한계입니다. 예를 들어, 일반적으로 최소 300개 메시지의 경우 오류 비율이 90%에 도달하면 이메일 전송이 3시간 동안 차단됩니다.

MX 관리에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#mx-configuration)을 참조하십시오.
