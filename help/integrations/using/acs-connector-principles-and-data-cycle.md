---
title: ACS 커넥터 원칙 및 데이터 주기
seo-title: ACS 커넥터 원칙 및 데이터 주기
description: ACS 커넥터 원칙 및 데이터 주기
seo-description: null
page-status-flag: never-activated
uuid: ea62ee69-042e-4c18-aaea-d65872d07dd9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 64d87bea-2376-4684-ac93-6ca56fe0f262
translation-type: tm+mt
source-git-commit: 75cbb8d697a95f4cc07768e6cf3585e4e079e171
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---


# ACS Connector principles and data cycle{#acs-connector-principles-and-data-cycle}

## 소개 {#introduction}

ACS 커넥터는 Adobe Campaign v7과 Adobe Campaign Standard을 연결시킵니다. 이 기능은 Campaign v7의 통합 기능으로, Campaign Standard에 데이터를 자동으로 복제하여 두 애플리케이션 중 최고의 성능을 제공합니다. Campaign v7에는 기본 마케팅 데이터베이스를 관리하는 고급 도구가 있습니다. Campaign v7의 데이터 복제를 통해 Campaign Standard은 사용자에게 친숙한 환경에서 리치 데이터를 활용할 수 있습니다.

![](assets/acs_connect_puzzle_link_01.png)

ACS 커넥터를 사용하면, Campaign Standard은 캠페인을 디자인, 타깃팅 및 실행하는 데 디지털 마케터가 사용하는 반면 Campaign v7은 데이터베이스 마케터와 같은 데이터 중심의 사용자를 위해 맞춤화된 제품입니다.

>[!IMPORTANT]
>
>ACS 커넥터는 Adobe Campaign Prime 제공 서비스의 일부로만 사용할 수 있습니다. Adobe Campaign Prime의 라이선스를 부여하는 방법에 대한 자세한 내용은 계정 관리자에게 문의하십시오.
>
>ACS 커넥터는 호스팅 및 하이브리드 아키텍처에서만 사용할 수 있습니다. 온-프레미스 설치에서는 사용할 수 없습니다.
>
>이 기능을 사용하려면 Campaign에 Adobe ID(IMS)을 연결해야 합니다. See [Connecting via an Adobe ID](../../integrations/using/about-adobe-id.md).

이 문서에서는 ACS 커넥터 기능을 제공합니다. 아래 섹션에서는 기능이 데이터를 복제하는 방법과 복제된 프로파일을 사용한 작업 방법에 대한 지침을 제공합니다.

* [프로세스](#process):ACS 커넥터 개요 및 데이터 복제 관리 방법
* [구현](#implementation):ACS 커넥터를 사용하는 방법에 대한 개요와 기본 및 고급 데이터를 복제하는 방법에 대한 지침입니다.
* [프로파일 동기화](../../integrations/using/synchronizing-profiles.md):프로필 복제 방법 및 프로필 사용 게재 생성 방법에 대한 지침
* [대상 동기화](../../integrations/using/synchronizing-audiences.md):Campaign v7에서 수신자 목록을 타깃팅한 다음 Campaign Standard에 대상으로 목록을 복제하는 방법에 대한 지침
* [웹 애플리케이션 동기화](../../integrations/using/synchronizing-web-applications.md):Campaign v7 웹 애플리케이션을 Campaign Standard에 연결하는 방법에 대한 지침
* [ACS 커넥터 문제 해결](../../integrations/using/troubleshooting-the-acs-connector.md):일반적인 문제에 대한 답변을 검토할 수 있습니다.

>[!NOTE]
>
>ACS 커넥터는 라이센스 계약에 따라 Campaign v7에 포함됩니다. ACS 커넥터를 사용하려면 Campaign v7과 Campaign Standard 간을 전환할 수 있는지 확인하십시오. 사용 중인 버전과 소프트웨어에 포함된 기능을 잘 모르는 경우 관리자에게 문의하십시오.

## 배합 색상 {#process}

### 데이터 복제 {#data-replication}

![](assets/acs_connect_flows_01.png)

ACS 커넥터는 Campaign v7에서 Campaign Standard으로 정기적으로 다음 항목을 복제합니다.

* **수신자**
* **구독**
* **서비스**
* **랜딩 페이지**

기본적으로 ACS 커넥터에 대한 주기적 복제는 15분마다 한 번씩 수행됩니다. 주기적 복제의 범위는 사용자의 요구 사항에 맞게 조정할 수 있습니다. 변경이 필요한 경우 컨설턴트에게 문의하십시오.

받는 사람, 구독, 서비스 및 랜딩 페이지에 대한 데이터 복제는 증분 방식이므로 새 받는 사람 및 기존 받는 사람에 대한 수정 사항만 Campaign v7에서 Campaign Standard으로 복제됩니다. 그러나 단일 인스턴스에서 대상을 위한 복제가 발생합니다. Campaign v7에서 대상을 만든 다음 한 번 Campaign Standard에 복제할 수 있습니다. 복제는 즉시 적용되며 일반 업데이트를 위해 구성할 수 없습니다. 자세한 내용은 대상 [동기화를 참조하십시오](../../integrations/using/synchronizing-audiences.md).

>[!NOTE]
>
>대용량의 데이터베이스를 처음 복제하는 데 몇 시간이 걸릴 수 있으므로 인내심을 갖고 기다려 주십시오. 그러나 이후 복제 작업은 증분 및 훨씬 빨라졌습니다.

ACS 커넥터는 Campaign Standard에서 Campaign v7으로 정기적으로 다음 항목을 복제합니다.

* **[!UICONTROL Delivery IDs]**
* **[!UICONTROL Email broad logs]**
* **[!UICONTROL Email tracking logs]**

배달 ID 및 이메일 로그를 복제하면 Campaign v7에서 v7 받는 사람의 배달 내역 및 추적 데이터에 액세스할 수 있습니다.

>[!IMPORTANT]
>
>이메일 브로드로그와 추적 로그만 Campaign Standard에서 Campaign v7으로 복제됩니다.

### 데이터 동기화 {#data-synchronization}

![](assets/acs_connect_flows_02.png)

ACS 커넥터는 Campaign v7과 Campaign Standard 간에 격리를 동기화합니다.

예를 들어 Campaign v7에서 Campaign Standard으로 복제된 프로필에 이메일 주소가 포함됩니다. 이메일 주소가 Campaign Standard으로 격리되면 다음 동기화 동안 데이터가 Campaign v7으로 전달됩니다. 검역에 대한 자세한 내용은 [검역관리](../../delivery/using/understanding-quarantine-management.md) 및 [Campaign Standard 검역관을 참조한다](https://docs.adobe.com/content/help/en/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html).

### 복제된 프로파일 사용 {#using-replicated-profiles}

복제된 프로필은 마케팅 캠페인의 타깃팅 워크플로우를 위해 Campaign Standard 및 Campaign v7에서 사용할 수 있습니다.

복제된 프로파일을 사용하여 Campaign Standard에서 배달을 보내는 방법에 대한 지침은 프로필 [동기화를 참조하십시오](../../integrations/using/synchronizing-profiles.md). Campaign v7과 Campaign Standard 간에 구독 취소 데이터를 공유하기 위한 추가 지침이 제공됩니다.

### 제한 사항 {#limitations}

복제된 프로필은 전달에 즉시 사용할 수 있지만 Campaign Standard에서는 특정 제한이 있습니다. 아래 항목을 검토하여 가장 효과적인 관리 방법을 살펴보십시오.

* **Campaign Standard에 대한 읽기 전용 프로필**:복제된 프로필은 Campaign Standard에서 읽기 전용입니다. 그러나 Campaign v7에서 수신자를 편집할 수 있으며 수정 사항은 ACS 커넥터로 Campaign Standard에서 자동으로 업데이트됩니다.
* **Campaign Standard에서 만든 프로필**:ACS 커넥터는 수신자 데이터를 Campaign v7에서 Campaign Standard으로 한 방향으로 복제합니다. 따라서 Campaign Standard에 있는 프로필은 Campaign v7에 복제되지 않습니다.
* **Campaign Standard에 대한 기본 수신자 데이터**:ACS 커넥터는 Campaign Standard에 적합한 수신자 데이터를 복제합니다. 여기에는 받는 사람의 이름, 주소, 이메일 주소, 휴대폰 번호, 집 전화 번호 및 기타 관련 연락처 정보가 포함됩니다. Campaign v7에서 사용할 수 있는 추가 수신자 필드 및 사용자 지정 타깃팅 테이블이 워크플로우에 중요한 경우 컨설턴트에게 문의하십시오.
* **격리된 프로필 가져오기**:연결하지 않으려는 프로필 목록은 Campaign v7 또는 격리된 프로필로 Campaign Standard으로 가져올 수 있습니다. 응용 프로그램 간의 격리 동기화에 프로필에 대한 상태가 포함되며 전달에 사용되지 않습니다.
* **Campaign Standard에서 서비스 가입 해지**:배달 구독 취소 선택은 Campaign Standard에서 Campaign v7으로 동기화되지 않습니다. 그러나, 구독 취소 링크를 Campaign v7으로 연결하도록 Campaign Standard 제공을 구성할 수 있습니다. 구독 취소 링크를 클릭하는 수신자에 대한 프로필은 Campaign v7에서 업데이트되며 데이터는 Campaign Standard에 복제됩니다. 구독 [취소 링크 변경을 참조하십시오](../../integrations/using/synchronizing-profiles.md#changing-the-unsubscription-link).
* 이메일 브로드로그와 추적 로그만 Campaign Standard에서 Campaign v7으로 복제됩니다.

### 과금 {#billing}

배송, Campaign v7 또는 Campaign Standard을 전송할 애플리케이션으로 인해 대금 청구에는 영향을 주지 않습니다. 청구 정보는 Campaign v7과 Campaign Standard 간에 조정됩니다. 따라서 두 애플리케이션을 모두 사용하여 동일한 수신자에게 전달을 전송하는 경우 여전히 하나의 활성 프로파일로 계산됩니다.

## 구현 {#implementation}

ACS 커넥터에 대해 두 가지 유형의 구현이 있습니다. 이 두 가지 모두 Adobe Campaign 컨설팅 팀이 수행합니다.

>[!IMPORTANT]
>
>이 섹션은 구현 프로세스 및 주요 단계에 대한 전체 보기를 제공하기 위해 전문가 사용자만을 대상으로 합니다.
>
>이러한 구현을 직접 수행하려고 시도하지 마십시오. Adobe Campaign 컨설턴트들에게만 따로 있습니다

기본 구현 **** 기능을 사용하면 수신자(기본 필드), 서비스 및 구독, 웹 애플리케이션 및 대상을 복제할 수 있습니다. 이는 Campaign v7에서 Campaign Standard으로 단방향 복제입니다.

추가 수신자 필드 또는 사용자 지정 수신자 테이블(예: 트랜잭션 테이블)이 있는 경우 **고급 구현을** 통해 보다 복잡한 사용 사례를 수행할 수 있습니다. 고급 [구현을 참조하십시오](#advanced-implementation).

### 패키지 설치 {#installing-the-package}

이 기능을 사용하려면 패키지를 **[!UICONTROL ACS Connector]** 설치해야 합니다. 이 작업은 Adobe 기술 관리자 또는 컨설턴트가 수행합니다.

ACS 커넥터와 관련된 모든 기술 요소는 탐색기의 **[!UICONTROL Administration > ACS Connector]** 노드에서 사용할 수 있습니다.

### 기술 및 복제 워크플로우 {#technical-and-replication-workflows}

패키지 설치 후 아래에서 두 가지 기술 워크플로우를 사용할 수 있습니다 **[!UICONTROL Administration > ACS Connector > Process]**.

>[!IMPORTANT]
>
>이러한 워크플로우를 수정하지 마십시오. 오류 또는 일시 중지되어서는 안 됩니다. 이 경우 Adobe Campaign 컨설턴트에게 문의하십시오.

![](assets/acs_connect_implementation_3.png)

* **[!UICONTROL `[ACS] Quarantine synchronization`]** (quarantineSync):이 워크플로우는 모든 격리 정보를 동기화합니다. Campaign v7의 모든 새로운 격리가 Campaign Standard에 복제됩니다. Campaign Standard의 모든 새로운 격리가 Campaign v7에 복제됩니다. 그러면 모든 제외 규칙이 Campaign v7과 Campaign Standard 간에 동기화됩니다.
* **[!UICONTROL `[ACS] Security group synchronization`]** (securityGroupSync):이 워크플로우는 권한 변환에 사용됩니다. 권한 [변환을 참조하십시오](#rights-conversion).

다음 복제 작업 과정은 &quot;사용 가능한&quot; 템플릿으로 사용할 수 있습니다. Adobe Campaign 컨설턴트가 해야 합니다.

![](assets/acs_connect_implementation_2.png)

* **[!UICONTROL `[ACS] Profile replication`]** (newProfileReplication):이 증분 워크플로우는 수신자를 Campaign Standard에 복제합니다. 기본적으로 모든 기본 수신자 필드를 복제합니다. 기본 수신자 [필드를 참조하십시오](#default-recipient-fields).
* **[!UICONTROL `[ACS] Service replication`]** (newServiceReplication):이러한 증분 워크플로우는 선택한 서비스를 Campaign Standard에 복제합니다. 웹 애플리케이션 [동기화 사용 사례를 참조하십시오](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] Landing pages replication`]** (newLandingPageReplication):이러한 증분 워크플로우는 선택한 웹 애플리케이션을 Campaign Standard으로 복제합니다. Campaign v7 웹 애플리케이션이 Campaign Standard에 랜딩 페이지로 표시됩니다. 웹 애플리케이션 [동기화 사용 사례를 참조하십시오](../../integrations/using/synchronizing-web-applications.md).
* **[!UICONTROL `[ACS] New replication`]** (newReplication):이 증분 워크플로우는 사용자 지정 테이블을 복제하는 데 사용할 수 있는 예입니다. 고급 [구현을 참조하십시오](#advanced-implementation).
* **[!UICONTROL `[ACS] Delivery-mesage replication`]** (newDlvMsgQualification):이 증분 워크플로우는 배달 메시지를 Campaign Standard에서 Campaign v7으로 복제합니다.
* **[!UICONTROL `[ACS] Profile delivery log replication`]** (newRcpDeliveryLogReplication):이 증분 워크플로우는 배달 ID, 이메일 확장 로그 및 이메일 추적 로그를 Campaign Standard에서 Campaign v7으로 복제합니다. Campaign Standard에서 Campaign v7의 nms:recipients 테이블에 포함된 프로필로 전송된 배달만 고려합니다.
* **[!UICONTROL `[ACS] New delivery log replication`]** (newRcpDeliveryLogReplication):이 증분 워크플로우는 배달 ID, 이메일 확장 로그 및 이메일 추적 로그를 Campaign Standard에서 Campaign v7으로 복제합니다. Campaign Standard에서 Campaign v7의 특정 테이블(nms:recipients 제외)에 속하는 프로필로 전송된 배달만 고려합니다.

### 기본 수신자 필드 {#default-recipient-fields}

추가 필드나 사용자 지정 테이블(예: 트랜잭션 테이블)이 있는 경우 기본적으로 복제되지 않습니다. 고급 구성을 수행해야 합니다. 고급 [구현을 참조하십시오](#advanced-implementation).

기본 구현과 함께 복제되는 수신자 필드 목록 아래에 있습니다. 기본적으로 제공되는 필드는 다음과 같습니다.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 소스 ID<br /> </td> 
   <td> @sourceId<br /> </td> 
  </tr> 
  <tr> 
   <td> 작성 날짜<br /> </td> 
   <td> @created<br /> </td> 
  </tr> 
  <tr> 
   <td> 수정 날짜<br /> </td> 
   <td> @lastModified<br /> </td> 
  </tr> 
  <tr> 
   <td> 이메일<br /> </td> 
   <td> @email<br /> </td> 
  </tr> 
  <tr> 
   <td> 성<br /> </td> 
   <td> @lastName<br /> </td> 
  </tr> 
  <tr> 
   <td> 이름<br /> </td> 
   <td> @firstName<br /> </td> 
  </tr> 
  <tr> 
   <td> 중간 이름<br /> </td> 
   <td> @middleName<br /> </td> 
  </tr> 
  <tr> 
   <td> 모바일<br /> </td> 
   <td> @mobilePhone<br /> </td> 
  </tr> 
  <tr> 
   <td> 생년월일<br /> </td> 
   <td> @birthDate<br /> </td> 
  </tr> 
  <tr> 
   <td> 성별<br /> </td> 
   <td> @gender<br /> </td> 
  </tr> 
  <tr> 
   <td> 인사말<br /> </td> 
   <td> @인사<br /> </td> 
  </tr> 
  <tr> 
   <td> 더 이상 연락하지 않음(모든 채널에서)<br /> </td> 
   <td> @blackList<br /> </td> 
  </tr> 
  <tr> 
   <td> 더 이상 이메일로 연락하지 않음<br /> </td> 
   <td> @blackListEmail<br /> </td> 
  </tr> 
  <tr> 
   <td> 더 이상 SMS로 연락하지 않습니다.<br /> </td> 
   <td> @blackListMobile<br /> </td> 
  </tr> 
  <tr> 
   <td> 전화<br /> </td> 
   <td> @phone<br /> </td> 
  </tr> 
  <tr> 
   <td> 팩스<br /> </td> 
   <td> @fax<br /> </td> 
  </tr> 
  <tr> 
   <td> 주소 1(아파트)<br /> </td> 
   <td> [location/@address1]<br /> </td> 
  </tr> 
  <tr> 
   <td> 주소 2<br /> </td> 
   <td> [location/@address2]<br /> </td> 
  </tr> 
  <tr> 
   <td> 주소 3(번호 및 주소)<br /> </td> 
   <td> [location/@address3]<br /> </td> 
  </tr> 
  <tr> 
   <td> 주소 4(군)<br /> </td> 
   <td> [location/@address4]<br /> </td> 
  </tr> 
  <tr> 
   <td> 우편 번호<br /> </td> 
   <td> [location/@zipCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 구/군/시<br /> </td> 
   <td> [location/@city]<br /> </td> 
  </tr> 
  <tr> 
   <td> 시/도 코드<br /> </td> 
   <td> [location/@stateCode]<br /> </td> 
  </tr> 
  <tr> 
   <td> 국가 번호<br /> </td> 
   <td> [location/@countryCode]<br /> </td> 
  </tr> 
 </tbody> 
</table>

### 권한 전환 {#rights-conversion}

권한은 Campaign v7 및 Campaign Standard에서 다르게 처리됩니다. Campaign v7에서는 권한 관리가 폴더 기반인 반면 Campaign Standard에서는 단위 액세스(조직/지역 단위)를 기반으로 합니다. Campaign Standard 사용자는 제한 컨텍스트를 포함하는 보안 그룹에 속합니다. 따라서 Campaign Standard과 일치하도록 Campaign v7 권한 시스템을 변환해야 합니다. 권한 변환을 수행하는 방법에는 여러 가지가 있습니다. 다음은 구현 예입니다.

1. 아래에서 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]****[!UICONTROL Synchronize]** 단추를 사용하여 모든 Campaign Standard 보안 그룹을 검색합니다. 기본 Campaign Standard 그룹은 제외됩니다.

   ![](assets/acs_connect_implementation_4.png)

1. 권한 관리가 폴더 기반인 경우 보안 그룹으로 이동하여 필요한 각 폴더 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]** 를 매핑합니다.

   ![](assets/acs_connect_implementation_5.png)

1. 그러면 복제 워크플로우에서 이 정보를 사용하고 각 객체에 해당 조직/지역 단위를 추가하여 복제합니다.

### 고급 구현 {#advanced-implementation}

이 섹션에서는 고급 구현의 몇 가지 가능성에 대해 설명합니다.

>[!IMPORTANT]
>
>이 정보는 일반 지침으로만 사용할 수 있습니다. 구현에 대해서는 Adobe Campaign 컨설턴트에게 문의하십시오.

고급 구현을 통해 고객의 요구 사항에 따라 맞춤형 복제 워크플로우를 추가할 수 있습니다. 다음은 몇 가지 예입니다.

* 배달 복제
* 캠페인 복제
* 프로그램 복제
* 시드 멤버 복제
* 트랜잭션 복제
* 등.

**수신자에게 확장 필드 복제**

기본 구현을 통해 기본 수신자 필드가 복제됩니다. 수신자 스키마에 추가한 사용자 정의 필드를 복제하려면 해당 필드를 식별해야 합니다.

1. 아래 **[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;에서 테이블에 타깃팅 매핑을 **[!UICONTROL nms:recipient]** 만듭니다.

   ![](assets/acs_connect_implementation_6.png)

1. 복제할 추가 필드 및 기타 필요한 정보(색인, 링크, 식별 키)를 선택합니다.

   ![](assets/acs_connect_implementation_7.png)

1. 전용 프로필 복제 작업 흐름을 엽니다(템플릿이 아니라 워크플로우 인스턴스 자체). 이러한 필드를 포함하도록 **[!UICONTROL Query]** 및 **[!UICONTROL Update data]** 활동을 수정합니다. 기술 [및 복제 워크플로우를 참조하십시오](#technical-and-replication-workflows).

   ![](assets/acs_connect_implementation_8.png)

   ![](assets/acs_connect_implementation_9.png)

**사용자 지정 프로필 테이블 복제**

기본 구현을 통해 기본 수신자 테이블이 복제됩니다. 사용자 지정 수신자 테이블을 추가한 경우 이 방법을 참조하십시오.

1. 아래 **[!UICONTROL Administration > ACS Connector > Data mapping]**&#x200B;에서 사용자 지정 프로필 테이블에 타깃팅 매핑을 만듭니다.

   ![](assets/acs_connect_implementation_10.png)

1. 복제할 식별 데이터, 색인, 링크 및 필드를 정의합니다.

   ![](assets/acs_connect_implementation_10.png)

1. 권한 관리가 폴더 기반인 경우 사용자 지정 테이블에 연결된 폴더의 보안 그룹 **[!UICONTROL Administration > ACS Connector > Rights management > Folder mapping]**&#x200B;을 찾아 정의합니다. 권한 [변환을 참조하십시오](#rights-conversion).
1. 사용자 **[!UICONTROL New replication]** 지정 테이블과 복제할 필드를 포함하려면 워크플로우(템플릿이 아니라 워크플로우 인스턴스 자체)를 사용합니다. 기술 [및 복제 워크플로우를 참조하십시오](#technical-and-replication-workflows).

