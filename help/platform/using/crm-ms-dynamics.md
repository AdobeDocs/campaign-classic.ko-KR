---
product: campaign
title: Campaign - Microsoft Dynamics CRM 커넥터
description: Campaign과 Microsoft Dynamics 연결 방법 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 3%

---

# Campaign과 Microsoft Dynamics 365 연결{#connect-to-msdyn}



이 페이지에서는 Campaign Classic에 연결하는 방법을 배웁니다. **Microsoft Dynamics CRM 365**.

가능한 배포는 **웹 API** (권장). 을(를) 참조하십시오 [아래 섹션](#microsoft-dynamics-implementation-step) Microsoft Dynamics와의 연결을 설정하는 단계를 알아봅니다.

데이터 동기화는 전용 워크플로우 활동을 통해 수행됩니다. [자세히 알아보기](../../platform/using/crm-data-sync.md)

## 구현 단계{#microsoft-dynamics-implementation-steps}

다음을 통해 Microsoft Dynamics 365를 Adobe Campaign과 함께 작업하도록 연결 **웹 API**, 다음 단계를 적용해야 합니다.

Microsoft Dynamics CRM에서:
1. Microsoft Dynamics 클라이언트 ID 가져오기
1. Microsoft Dynamics 인증서 키 식별자 및 키 ID 생성
1. 권한 구성
1. 앱 사용자 만들기
1. 개인 키 인코딩

[이 섹션에서 자세히 알아보십시오](#config-crm-microsoft)

Campaign Classic:
1. 새 외부 계정 만들기
1. Microsoft Dynamics 설정으로 외부 계정 구성
1. 구성 마법사를 사용하여 테이블을 매핑하고 열거형을 동기화합니다.
1. 동기화 워크플로우 만들기

[이 섹션에서 자세히 알아보십시오](#configure-acc-for-microsoft)


>[!CAUTION]
> Microsoft Dynamics와 Adobe Campaign을 연결할 때 다음을 수행할 수 없습니다.
> * CRM의 동작을 변경하고 Adobe Campaign과의 호환성 문제를 초래할 수 있는 플러그인을 설치합니다.
> * 여러 열거형 선택


## Microsoft Dynamics CRM 구성 {#config-crm-microsoft}

액세스 토큰과 계정을 설정하는 키를 생성하려면 로그인해야 합니다. [Microsoft Azure 디렉터리](https://portal.azure.com) 사용 **전역 관리자** 자격 증명. 그런 다음 아래에 설명된 단계를 수행합니다.

### Microsoft Dynamics 클라이언트 ID 가져오기 {#get-client-id-microsoft}

클라이언트 ID를 가져오려면 Azure Active Directory에 앱을 등록해야 합니다. 클라이언트 ID는 애플리케이션 ID와 동일합니다.

1. 다음으로 이동 **Azure Active Directory > 앱 등록**, 및 클릭  **새 애플리케이션 등록**.
1. 인스턴스를 식별하는 데 도움이 될 수 있는 고유한 이름을 지정합니다. 예: **adobeccampaign`<instance identifier>`**.
1. 선택 **애플리케이션 유형** 다음으로: **웹 앱/API**.
1. 사용 `http://localhost` 대상 **로그온 URL**.

저장하면 **애플리케이션 ID** - Campaign의 클라이언트 식별자입니다.

[이 페이지](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)에서 자세히 알아보십시오.

### Microsoft Dynamics 인증서 키 식별자 및 키 ID 생성 {#config-certificate-key-id}

을(를) 가져오려면 **인증서 키 식별자(customKeyIdentifier)** 및 **키 ID (keyId)**&#x200B;을(를) 클릭하고 아래 단계를 수행합니다.

1. 다음으로 이동 **Azure Active Directory > 앱 등록** 앞에서 만든 응용 프로그램을 선택합니다.
1. 클릭 **인증서 및 암호**.
1. 클릭 **인증서 업로드** 그런 다음 생성된 공개 인증서를 찾아 업로드합니다.
1. 인증서를 생성하려면 openssl을 사용합니다.

   예제:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >여기서 일수를 변경할 수 있습니다. `-days 365`: 더 긴 인증서 유효 기간을 위한 코드 샘플입니다.

1. 그런 다음 base64에서 인코딩해야 합니다. 이렇게 하려면 Base64 인코더의 도움을 사용하거나 명령줄을 사용합니다 `base64 -w0 private.key` Linux용

1. 을(를) 클릭합니다 **매니페스트** 링크: **인증서 키 식별자(customKeyIdentifier)** 및 **키 ID (keyId)**.

다음 **인증서 키 식별자(customKeyIdentifier)** 및 **키 ID (keyId)** 인증서를 사용하여 Microsoft Dynamics CRM 외부 계정을 구성하는 데 나중에 필요합니다 **[!UICONTROL CRM O-Auth type]**.

### 권한 구성 {#config-permissions-microsoft}

**1단계**: 구성 **필수 권한** (생성된 앱).

1. 다음으로 이동 **Azure Active Directory > 앱 등록** 앞에서 만든 응용 프로그램을 선택합니다.
1. 클릭 **설정** 왼쪽 위에 있습니다.
1. 날짜 **필수 권한**, 클릭 **추가** 및 **API > Dynamics CRM Online 선택**.
1. 클릭 **선택**, 활성화 **Dynamics 365를 조직 사용자로 액세스** 확인란 및 클릭 **선택**.
1. 그런 다음 앱에서 **매니페스트** 다음 아래에 **관리** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. 다음에서 **매니페스트** 편집기, 설정 `allowPublicClient` 다음에서 속성 `null` 끝 `true` 및 클릭 **저장**.

**2단계**: 관리자 동의 부여

1. 다음으로 이동 **Azure Active Directory > 엔터프라이즈 애플리케이션**.

1. 테넌트 전체 관리자 동의를 부여할 애플리케이션을 선택합니다.

1. 왼쪽 창 메뉴에서 다음을 선택합니다. **권한** 아래에 **보안**.

1. 클릭 **관리자 동의 부여**.

자세한 내용은 다음을 참조하십시오. [Azure 설명서](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### 앱 사용자 만들기 {#create-app-user-microsoft}

>[!NOTE]
>
> 이 단계는 와 함께 선택 사항입니다. **[!UICONTROL Password credentials]** 인증.

앱 사용자는 위에 등록된 애플리케이션이 사용할 사용자입니다. 위에 등록된 앱을 사용하여 Microsoft Dynamics에 대한 모든 변경 작업은 이 사용자를 통해 수행됩니다.

**1단계**: azure active directory에서 비대화형 사용자 만들기

1. 클릭 **Azure Active Directory > 사용자** 및 클릭 **새 사용자**.
1. 사용할 올바른 이름을 지정하십시오. 사용자 이름은 이메일 형식이어야 합니다.
1. 선택 **Dynamics 365 관리자** 다음에서 **디렉터리 역할**.

**2단계**: 생성된 사용자에게 적절한 라이선스 할당

1. 출처: [Microsoft Azure](https://portal.azure.com), 클릭 **관리 앱**.
1. 다음으로 이동 **사용자 > 활성 사용자** 을(를) 클릭하고 새로 생성된 사용자를 클릭합니다.
1. 클릭 **제품 라이선스 편집** 및 선택 **Dynamics 365 고객 참여 계획**.
1. Click **Close**.

**3단계**: Dynamics CRM에서 애플리케이션 사용자 만들기

1. 출처: [Microsoft Azure](https://portal.azure.com), 다음으로 이동 **설정 > 보안 > 사용자**.
1. 드롭다운을 클릭하고 을 선택합니다. **애플리케이션 사용자** 및 클릭 **신규**.
1. 위의 active directory에서 만든 사용자와 동일한 사용자 이름 사용

   >[!NOTE]
   >
   >동일한 이름을 사용하면 중복 키 오류가 발생하므로 이 단계가 필요한지 여부가 확인될 때까지 다른 사용자 이름을 사용하여 계속 진행하십시오.

1. 할당 **애플리케이션 ID** 대상 [이전에 만든 응용 프로그램](#get-client-id-microsoft).
1. 클릭 **역할 관리** 및 선택 **시스템 관리자** 역할을 사용자에게 부여합니다.

## Campaign 구성 {#configure-acc-for-microsoft}

>[!NOTE]
>
> 의 서비스 해제 게시 [Microsoft의 RDS](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint), 온-프레미스 및 Office 365 유형의 CRM 배포는 더 이상 Campaign과 호환되지 않습니다. Adobe Campaign은 이제 CRM 버전에 대한 웹 API 배포만 지원합니다 **Dynamic CRM 365**. [자세히 알아보기](../../rn/using/deprecated-features.md#crm-connectors)

Microsoft Dynamics 365와 Campaign을 연결하려면 전용 을(를) 만들고 구성해야 합니다 **[!UICONTROL External Account]** Campaign에서

1. 다음으로 이동 **[!UICONTROL Administration > Platform > External accounts]**.

1. 다음 항목 선택 **[!UICONTROL Microsoft Dynamics CRM]** 외부 계정입니다. **[!UICONTROL Enabled]** 옵션을 선택합니다.

1. Microsoft Dynamics 365 및 Campaign에 연결하는 데 필요한 정보를 입력합니다.

   >[!NOTE]
   >
   >다음을 포함한 Microsoft Dynamics CRM 외부 계정 구성 **[!UICONTROL CRM O-Auth type]** 세부 정보 [이 섹션에서](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. **[!UICONTROL Microsoft CRM configuration wizard...]** 링크를 클릭합니다. Adobe Campaign은 Microsoft Dynamics 데이터 템플릿에서 테이블을 자동으로 검색합니다.

   ![](assets/crm_connectors_msdynamics_02.png)

1. 복구할 테이블을 선택합니다.

   ![](assets/crm_connectors_msdynamics_03.png)

1. 클릭 **[!UICONTROL Next]** 를 클릭하여 해당 스키마를 생성할 수 있습니다.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >구성을 승인하려면 Adobe Campaign 콘솔의 연결을 끊거나 다시 연결해야 합니다.

   Adobe Campaign에서 일치하는 데이터 스키마를 사용할 수 있는지 확인할 수 있습니다.

   ![](assets/crm_connectors_msdynamics_05.png)

1. 다음을 클릭합니다. **[!UICONTROL Synchronizing enumerations...]** Adobe Campaign과 Microsoft Dynamics 간의 열거 동기화를 시작하는 링크입니다.

   ![](assets/crm_connectors_msdynamics_06.png)

이제 Campaign과 Microsoft Dynamics가 연결되었습니다. 두 시스템 간에 데이터 동기화를 설정할 수 있습니다. 다음에서 자세히 알아보기 [데이터 동기화](../../platform/using/crm-data-sync.md) 섹션.

>[!NOTE]
>
> 을(를) 허용 목록에 추가하다에 추가해야 합니다. 서버 URL과 `login.microsoftonline.com` 을 참조하십시오. URL 권한을 구성하는 방법에 대한 자세한 내용은 다음을 참조하십시오. [페이지](../../installation/using/url-permissions.md).

## 지원되는 필드 데이터 유형 {#ms-dyn-supported-types}

Microsoft Dynamics 365의 경우 지원되는/지원되지 않는 특성 유형은 다음과 같습니다.


| 속성 유형 | 지원됨 |
| --------------------------------------------------------------------------------- | --------- |
| 기본 유형 : 부울, 날짜/시간, 십진수, 부동 소수점, 더블, 정수, bigint , 문자열 | 예 |
| 금액(두 배로 표시) | 예 |
| memo, entityname , primarykey, uniqueidentifier(문자열로 표시) | 예 |
| 상태, 선택 목록(가능한 값은 열거형으로 저장됨), 상태(문자열) | 예 |
| 소유자(문자열로) | 예 |
| 조회(단일 엔티티 참조 조회만) | 예 |
| 고객 | 아니요 |
| 관련 항목 | 아니요 |
| PartyList | 아니요 |
| ManagedProperty | 아니요 |
| 다중 선택 옵션 집합 | 아니요 |
