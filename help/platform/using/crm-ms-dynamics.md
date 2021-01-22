---
solution: Campaign Classic
product: campaign
title: Microsoft Dynamics CRM Connector
description: Connect Campaign 및 Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 521bc3bf9b2507947007d7f458679275d407f910
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 1%

---


# Connect 캠페인 및 Microsoft Dynamics 365{#connect-to-msdyn}

이 페이지에서는 Campaign Classic을 **Microsoft Dynamics CRM 365**&#x200B;에 연결하는 방법을 알아봅니다.

배포 가능 항목:

* 를 통해 **웹 API**(권장) Microsoft Dynamics와의 연결을 설정하는 단계를 살펴보려면 [ 아래 섹션을 참조하십시오.](#microsoft-dynamics-implementation-step)
* **Office 365**&#x200B;과 함께 사용할 수 있습니다. 이 통합을 설정하는 주요 단계를 살펴보려면 [이 비디오](#microsoft-dynamics-office-365)를 참조하십시오.
* **온-프레미스** 배포의 경우 Office 365 키 단계를 적용합니다.

데이터 동기화는 전용 워크플로우 활동을 통해 수행됩니다. [자세히 알아보기](../../platform/using/crm-data-sync.md)


>[!NOTE]
>
> Campaign과 호환되는 CRM 시스템 버전은 [호환성 매트릭스](../../rn/using/compatibility-matrix.md#CRMconnectors)에 나열됩니다.


## 구현 단계{#microsoft-dynamics-implementation-steps}

**웹 API**&#x200B;를 통해 Adobe Campaign에서 작업하도록 Microsoft Dynamics 365를 연결하려면 다음 단계를 적용해야 합니다.

Microsoft Dynamics CRM에서:
1. Microsoft Dynamics 클라이언트 ID 가져오기
1. Microsoft Dynamics 클라이언트 암호 생성
1. 권한 구성
1. 앱 사용자 만들기
1. 개인 키 인코딩

[이 섹션에 대한 자세한 내용](#config-crm-microsoft)

Campaign Classic:
1. 새 외부 계정 만들기
1. Microsoft Dynamics 설정으로 외부 계정 구성
1. 구성 마법사를 사용하여 테이블을 매핑하고 열거형을 동기화합니다.
1. 동기화 워크플로우 만들기

[이 섹션에 대한 자세한 내용](#configure-acc-for-microsoft)


>[!CAUTION]
> Adobe Campaign을 Microsoft Dynamics와 연결할 때 다음과 같은 작업을 수행할 수 없습니다.
> * CRM 동작을 변경하고 Adobe Campaign와의 호환성 문제를 초래할 수 있는 플러그인 설치
> * 여러 열거형 선택

>



## Microsoft Dynamics CRM {#config-crm-microsoft} 구성

액세스 토큰과 키를 생성하여 계정을 설정하려면 **전역 관리자** 자격 증명을 사용하여 [Microsoft Azure 디렉터리](https://portal.azure.com)에 로그인해야 합니다. 그런 다음 아래 설명된 단계를 수행합니다.

### Microsoft Dynamics 클라이언트 ID {#get-client-id-microsoft} 가져오기

클라이언트 ID를 가져오려면 Azure Active Directory에서 앱을 등록해야 합니다. 클라이언트 ID는 응용 프로그램 ID와 동일합니다.

1. **Azure Active Directory > 앱 등록**&#x200B;으로 이동하고 **새 응용 프로그램 등록**&#x200B;을 클릭합니다.
1. **adobeccampaign`<instance identifier>`**&#x200B;과 같은 인스턴스를 식별하는 데 도움이 되는 고유한 이름을 지정합니다.
1. **응용 프로그램 유형**&#x200B;을 **웹 앱 / API**&#x200B;로 선택합니다.
1. **사인온 URL**&#x200B;에 `http://localhost`을(를) 사용하십시오.

저장하면 캠페인에 대한 클라이언트 식별자인 **응용 프로그램 ID**&#x200B;가 표시됩니다.

[이 페이지](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)에서 자세히 알아보십시오.

### Microsoft Dynamics 클라이언트 암호 생성 {#config-client-secret-microsoft}

클라이언트 암호는 클라이언트 ID에 고유한 키입니다. 인증서 키 식별자를 받으려면 아래 단계를 따르십시오.

1. **Azure Active Directory > 앱 등록**&#x200B;으로 이동하여 이전에 만든 응용 프로그램을 선택합니다.
1. **인증서 및 암호**&#x200B;를 클릭합니다.
1. **인증서 업로드**&#x200B;를 클릭한 다음 생성된 공개 인증서를 찾아 업로드합니다.
1. 인증서를 생성하려면 openssl을 사용할 수 있습니다.

   예제:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. **manifest** 링크를 클릭하여 **인증서 키 식별자** 및 **키 ID**&#x200B;를 가져옵니다.

### 권한 구성 {#config-permissions-microsoft}

만든 앱에 대해 **필수 권한**&#x200B;을 구성해야 합니다.

1. **Azure Active Directory > 앱 등록**&#x200B;으로 이동하여 이전에 만든 응용 프로그램을 선택합니다.
1. 왼쪽 상단에서 **설정**&#x200B;을 클릭합니다.
1. **필수 권한**&#x200B;에서 **추가** 및 **API > Dynamics CRM Online**&#x200B;을 선택합니다.
1. 그런 다음 **선택**&#x200B;을 클릭하고 **조직 사용자로 Dynamics 365에 액세스** 확인란을 활성화하고 **선택**&#x200B;을 클릭합니다.

### 앱 사용자 {#create-app-user-microsoft} 만들기

앱 사용자는 위에 등록된 애플리케이션에서 사용할 사용자입니다. 위에 등록된 앱을 사용하여 Microsoft Dynamics에 변경한 내용은 이 사용자를 통해 수행됩니다.

**1단계**:Azure active directory에서 비대화형 사용자 만들기

1. **Azure Active Directory > 사용자**&#x200B;를 클릭하고 **새 사용자**&#x200B;를 클릭합니다.
1. 사용할 이름을 지정하고 사용자 이름은 이메일 형식이어야 합니다.
1. **디렉터리 역할**&#x200B;에서 **Dynamics 365 관리자**&#x200B;를 선택합니다.

**2단계**:생성된 사용자에게 적절한 라이선스 할당

1. [Microsoft Azure](https://portal.azure.com)에서 **관리 앱**&#x200B;을 클릭합니다.
1. **사용자 > 활성 사용자**&#x200B;로 이동하고 새로 만든 사용자를 클릭합니다.
1. **제품 라이센스 편집**&#x200B;을 클릭하고 **Dynamics 365 고객 참여 플랜**&#x200B;을 선택합니다.
1. **닫기**&#x200B;를 클릭합니다.

**3단계**:Dynamics CRM에서 응용 프로그램 사용자 만들기

1. [Microsoft Azure](https://portal.azure.com)에서 **설정 > 보안 > 사용자**&#x200B;로 이동합니다.
1. 드롭다운을 클릭하고 **응용 프로그램 사용자**&#x200B;를 선택하고 **새로 만들기**&#x200B;를 클릭합니다.
1. 위의 Active Directory에서 만든 사용자와 동일한 사용자 이름을 사용합니다.

   >[!NOTE]
   >
   >동일한 이름을 사용하면 키 오류가 중복될 수 있으므로 이 단계가 필요한지 확인할 때까지 다른 사용자 이름을 사용하고 계속 진행합니다.

1. [이전에 만든 응용 프로그램에 대해 **응용 프로그램 ID**&#x200B;을 할당합니다.](#get-client-id-microsoft)
1. **역할 관리**&#x200B;를 클릭하고 사용자에게 **시스템 관리자** 역할을 선택합니다.

## 캠페인 구성 {#configure-acc-for-microsoft}

Microsoft Dynamics 365 및 Campaign을 연결하려면 Campaign에서 전용 외부 계정을 만들고 구성해야 합니다.

1. **[!UICONTROL Administration > Platform > External accounts]**&#x200B;으로 이동합니다.

1. 새 외부 계정을 만들고 **[!UICONTROL Microsoft Dynamics CRM]** 유형과 **[!UICONTROL Enable]** 옵션을 선택합니다.

1. **[!UICONTROL Web API]** 배포 유형을 선택합니다.

   Adobe Campaign Classic은 **[!UICONTROL Certificate]** 또는 **[!UICONTROL Password Credentials]**&#x200B;의 인증을 위해 OAuth 프로토콜이 있는 Dynamics 365 REST 인터페이스를 지원합니다.

   외부 계정을 구성하려면 Azure Directory에서 이전에 정의된 [ 설정을 사용하십시오.](#get-client-id-microsoft)

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >Microsoft Dynamics CRM 외부 계정 구성은 이 섹션](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)에서 [에 자세히 설명되어 있습니다.

1. **[!UICONTROL Microsoft CRM configuration wizard...]** 링크를 클릭합니다.Adobe Campaign은 Microsoft Dynamics 데이터 템플릿에서 표를 자동으로 검색합니다.

   ![](assets/crm_connectors_msdynamics_02.png)

1. 복구할 표를 선택합니다.

   ![](assets/crm_connectors_msdynamics_03.png)

1. **[!UICONTROL Next]**&#x200B;을 클릭하여 해당 스키마 만들기를 시작합니다.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >구성을 승인하려면 Adobe Campaign 콘솔에 연결 해제/다시 연결해야 합니다.

   일치하는 데이터 스키마를 Adobe Campaign에서 사용할 수 있는지 확인할 수 있습니다.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Adobe Campaign과 Microsoft Dynamics 간에 열거형 동기화를 시작하려면 **[!UICONTROL Synchronizing enumerations...]** 링크를 클릭합니다.

   ![](assets/crm_connectors_msdynamics_06.png)

이제 Campaign과 Microsoft Dynamics가 연결되어 있습니다. 두 시스템 간의 데이터 동기화를 설정할 수 있습니다. [데이터 동기화](../../platform/using/crm-data-sync.md) 섹션에서 자세한 내용을 살펴보십시오.

## Microsoft Dynamics CRM Office 365 통합 구성{#microsoft-dynamics-office-365}

이 비디오를 통해 Office 365 배포의 컨텍스트에서 Adobe Campaign Classic과 Dynamics 365를 통합하는 방법을 알아보십시오.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


## 지원되는 필드 데이터 유형 {#ms-dyn-supported-types}

Microsoft Dynamics 365에서 지원되거나 지원되지 않는 특성 유형은 아래에 나열되어 있습니다.


| 속성 유형 | 지원됨 |
| --------------------------------------------------------------------------------- | --------- |
| 기본 유형:boolean, datetime, decimal, float, double, integer, bigint, string | 예 |
| 금액(이중) | 예 |
| 메모, entityname, 기본 키, 고유 식별자(문자열) | 예 |
| 상태, 선택 목록(열거형에 가능한 값을 저장함), 상태(문자열) | 예 |
| 소유자(문자열로) | 예 |
| 조회(단일 엔티티 참조 조회만) | 예 |
| 고객 | 아니요 |
| 관련 항목 | 아니요 |
| PartyList | 아니요 |
| ManagedProperty | 아니요 |
