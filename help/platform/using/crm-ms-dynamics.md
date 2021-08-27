---
product: campaign
title: Campaign - Microsoft Dynamics CRM 커넥터
description: Campaign 및 Microsoft Dynamics 연결
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 3%

---

# Campaign 및 Microsoft Dynamics 365 연결{#connect-to-msdyn}

![](../../assets/common.svg)

이 페이지에서는 Campaign Classic을 **Microsoft Dynamics CRM 365**&#x200B;에 연결하는 방법을 알아봅니다.

가능한 배포는 **웹 API**&#x200B;를 통해 수행할 수 있습니다(권장). Microsoft Dynamics와의 연결을 설정하는 단계를 알아보려면 [ 아래 섹션을 참조하십시오.](#microsoft-dynamics-implementation-step)

데이터 동기화는 전용 워크플로우 활동을 통해 수행됩니다. [자세히 알아보기](../../platform/using/crm-data-sync.md)

## 구현 단계{#microsoft-dynamics-implementation-steps}

**웹 API**&#x200B;를 통해 Adobe Campaign에서 작동하도록 Microsoft Dynamics 365를 연결하려면 다음 단계를 적용해야 합니다.

Microsoft Dynamics CRM에서:
1. Microsoft Dynamics 클라이언트 ID 가져오기
1. Microsoft Dynamics 인증서 키 식별자 및 키 ID 생성
1. 권한 구성
1. 앱 사용자 만들기
1. 개인 키 인코딩

[이 섹션에서 자세히 알아보기](#config-crm-microsoft)

Campaign Classic:
1. 새 외부 계정 만들기
1. Microsoft Dynamics 설정으로 외부 계정 구성
1. 구성 마법사를 사용하여 테이블을 매핑하고 열거형을 동기화합니다
1. 동기화 워크플로우 만들기

[이 섹션에서 자세히 알아보기](#configure-acc-for-microsoft)


>[!CAUTION]
> Adobe Campaign과 Microsoft Dynamics를 연결할 때 다음을 수행할 수 없습니다.
> * CRM의 동작을 변경하고 Adobe Campaign와의 호환성 문제가 발생할 수 있는 플러그인을 설치합니다
> * 여러 열거형 선택


## Microsoft Dynamics CRM 구성 {#config-crm-microsoft}

액세스 토큰 및 키를 생성하여 계정을 설정하려면 **전역 관리자** 자격 증명을 사용하여 [Microsoft Azure 디렉토리](https://portal.azure.com)에 로그인해야 합니다. 그런 다음 아래 설명된 단계를 수행합니다.

### Microsoft Dynamics 클라이언트 ID 가져오기 {#get-client-id-microsoft}

클라이언트 ID를 가져오려면 Azure Active Directory에서 앱을 등록해야 합니다. 클라이언트 ID는 애플리케이션 ID와 동일합니다.

1. **Azure Active Directory > 앱 등록**&#x200B;으로 이동하고 **새 응용 프로그램 등록**&#x200B;을 클릭합니다.
1. **adobecampaign`<instance identifier>`**&#x200B;과 같이 인스턴스를 식별하는 데 도움이 되는 고유한 이름을 지정합니다.
1. **애플리케이션 유형**&#x200B;을 **웹 앱 / API**&#x200B;로 선택합니다.
1. **사인온 URL**&#x200B;에 `http://localhost`을 사용하십시오.

저장하면 Campaign에 대한 클라이언트 식별자인 **애플리케이션 ID**&#x200B;가 제공됩니다.

[이 페이지](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)에서 자세히 알아보십시오.

### Microsoft Dynamics 인증서 키 식별자 및 키 ID 생성 {#config-certificate-key-id}

**인증서 키 식별자(customKeyIdentifier)** 및 **키 ID(keyId)**&#x200B;를 가져오려면 아래 단계를 수행하십시오.

1. **Azure Active Directory > 앱 등록**&#x200B;으로 이동하여 이전에 만든 응용 프로그램을 선택합니다.
1. **Certificates 및 Secret**&#x200B;을 클릭합니다.
1. **인증서 업로드**&#x200B;를 클릭한 다음 생성된 공개 인증서를 찾아 업로드합니다.
1. 인증서를 생성하기 위해 openssl을 사용할 수 있습니다.

   예제:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >여기서 `-days 365` 일 수는 더 긴 인증서 유효 기간 동안 코드 샘플에서 변경할 수 있습니다.

1. 그런 다음 base64에서 인코딩해야 합니다. 이렇게 하려면 Base64 인코더의 도움을 받거나 Linux용 명령줄 `base64 -w0 private.key`을 사용할 수 있습니다.

1. **Manifest** 링크를 클릭하여 **인증서 키 식별자(customKeyIdentifier)** 및 **키 ID(keyId)**&#x200B;를 가져옵니다.

**인증서 키 식별자(customKeyIdentifier)** 및 **키 ID(keyId)**&#x200B;가 나중에 **[!UICONTROL CRM O-Auth type]** 인증서를 사용하여 Microsoft Dynamics CRM 외부 계정을 구성해야 합니다.

### 권한 구성 {#config-permissions-microsoft}

**1단계**: 생성된  **앱** 에 대한 필수 권한을 구성합니다.

1. **Azure Active Directory > 앱 등록**&#x200B;으로 이동하여 이전에 만든 응용 프로그램을 선택합니다.
1. 왼쪽 상단에 있는 **설정**&#x200B;을 클릭합니다.
1. **필수 권한**&#x200B;추가&#x200B;**및** API > Dynamics CRM Online **을 클릭합니다.**
1. **선택**&#x200B;을 클릭하고, **조직 사용자로 Dynamics 365에 액세스** 확인란을 활성화하고 **선택**&#x200B;을 클릭합니다.
1. 그런 다음 앱에서 **관리** 메뉴에서 **매니페스트**&#x200B;를 선택합니다.

1. **Manifest** 편집기에서 `allowPublicClient` 속성을 `null`에서 `true`로 설정하고 **저장**&#x200B;을 클릭합니다.

**2단계**: 관리자 동의 부여

1. **Azure Active Directory > Enterprise 응용 프로그램**&#x200B;으로 이동합니다.

1. 임차인 전체 관리자 동의를 부여할 애플리케이션을 선택합니다.

1. 왼쪽 창 메뉴에서 **보안**&#x200B;에서 **권한**&#x200B;을 선택합니다.

1. **관리자 동의 부여**&#x200B;를 클릭합니다.

자세한 내용은 [Azure 설명서](https://docs.microsoft.com/en-us/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal)를 참조하십시오.

### 앱 사용자 만들기 {#create-app-user-microsoft}

>[!NOTE]
>
> 이 단계는 **[!UICONTROL Password credentials]** 인증 시 선택 사항입니다.

앱 사용자는 위에 등록된 애플리케이션이 사용할 사용자입니다. 위에 등록된 앱을 사용하여 Microsoft Dynamics에 변경한 내용은 이 사용자를 통해 수행됩니다.

**1단계**: Azure active directory에서 비대화형 사용자 만들기

1. **Azure Active Directory > 사용자**&#x200B;를 클릭하고 **새 사용자**&#x200B;를 클릭합니다.
1. 사용할 이름을 지정하고 사용자 이름은 이메일 형식이어야 합니다.
1. **디렉터리 역할**&#x200B;에서 **Dynamics 365 관리자**&#x200B;를 선택합니다.

**2단계**: 생성된 사용자에게 적절한 라이센스 할당

1. [Microsoft Azure](https://portal.azure.com)에서 **관리 앱**&#x200B;을 클릭합니다.
1. **사용자 > 활성 사용자**&#x200B;로 이동하여 새로 만든 사용자를 클릭합니다.
1. **제품 라이선스 편집**&#x200B;을 클릭하고 **Dynamics 365 고객 참여 계획**&#x200B;을(를) 선택합니다.
1. **닫기**&#x200B;를 클릭합니다.

**3단계**: Dynamics CRM에서 응용 프로그램 사용자 만들기

1. [Microsoft Azure](https://portal.azure.com)에서 **설정 > 보안 > 사용자**&#x200B;로 이동합니다.
1. 드롭다운을 클릭하고 **응용 프로그램 사용자**&#x200B;를 선택한 다음 **새로 만들기**&#x200B;를 클릭합니다.
1. 위의 active directory에서 만든 사용자와 동일한 사용자 이름을 사용합니다

   >[!NOTE]
   >
   >동일한 이름을 사용하면 중복 키 오류가 발생하므로 이 단계가 필요한지 여부를 확인할 때까지 다른 사용자 이름을 사용하여 계속 진행합니다.

1. [이전에 만든 응용 프로그램에 대해 **응용 프로그램 ID**&#x200B;를 할당합니다](#get-client-id-microsoft).
1. **역할 관리**&#x200B;를 클릭하고 **시스템 관리자** 역할을 사용자에게 선택합니다.

## Campaign 구성 {#configure-acc-for-microsoft}

>[!NOTE]
>
> Microsoft](https://docs.microsoft.com/en-us/previous-versions/dynamicscrm-2016/developers-guide/dn281891(v=crm.8)?redirectedfrom=MSDN#microsoft-dynamics-crm-2011-endpoint)에서 [RDS의 제거를 게시하면 온-프레미스 및 Office 365 유형의 CRM 배포는 더 이상 Campaign과 호환되지 않습니다. 이제 Adobe Campaign은 CRM 버전 **Dynamic CRM 365**&#x200B;에 대해서만 웹 API 배포를 지원합니다. [자세히 알아보기](../../rn/using/deprecated-features.md#crm-connectors)

Microsoft Dynamics 365 및 Campaign을 연결하려면 Campaign에서 전용 **[!UICONTROL External Account]**&#x200B;을(를) 만들고 구성해야 합니다.

1. **[!UICONTROL Administration > Platform > External accounts]**&#x200B;으로 이동합니다.

1. **[!UICONTROL Microsoft Dynamics CRM]** 외부 계정을 선택합니다. **[!UICONTROL Enabled]** 옵션을 선택합니다.

1. Microsoft Dynamics 365 및 Campaign을 연결하는 데 필요한 정보를 입력합니다.

   >[!NOTE]
   >
   >각 **[!UICONTROL CRM O-Auth type]**&#x200B;이 있는 Microsoft Dynamics CRM 외부 계정 구성은 이 섹션](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)에 [에 자세히 설명되어 있습니다.

   ![](assets/crm-ms-dynamics-ext-account.png)

1. **[!UICONTROL Microsoft CRM configuration wizard...]** 링크를 클릭합니다. Adobe Campaign은 Microsoft Dynamics 데이터 템플릿에서 테이블을 자동으로 검색합니다.

   ![](assets/crm_connectors_msdynamics_02.png)

1. 복구할 테이블을 선택합니다.

   ![](assets/crm_connectors_msdynamics_03.png)

1. **[!UICONTROL Next]** 을 클릭하여 해당 스키마 만들기를 시작합니다.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >구성을 승인하려면 Adobe Campaign 콘솔에서 연결을 끊거나 다시 연결해야 합니다.

   일치하는 데이터 스키마를 Adobe Campaign에서 사용할 수 있는지 확인할 수 있습니다.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Adobe Campaign과 Microsoft Dynamics 간에 열거형 동기화를 시작하려면 **[!UICONTROL Synchronizing enumerations...]** 링크를 클릭하십시오.

   ![](assets/crm_connectors_msdynamics_06.png)

이제 Campaign과 Microsoft Dynamics가 연결되었습니다. 두 시스템 간에 데이터 동기화를 설정할 수 있습니다. 자세한 내용은 [데이터 동기화](../../platform/using/crm-data-sync.md) 섹션에서 알아보십시오.

>[!NOTE]
>
> 허용 목록에 다음 두 URL을 추가해야 합니다. 서버 구성의 서버 URL 및 `login.microsoftonline.com`

## 지원되는 필드 데이터 유형 {#ms-dyn-supported-types}

Microsoft Dynamics 365의 경우 지원되는/지원되지 않는 특성 유형은 아래에 나와 있습니다.


| 속성 유형 | 지원됨 |
| --------------------------------------------------------------------------------- | --------- |
| 기본 유형 : 부울, datetime, decimal, float, double, 정수, bigint, 문자열 | 예 |
| 돈(이중) | 예 |
| 메모, entityname , primarykey, uniqueidentifier (as string) | 예 |
| 상태, picklist(가능한 값을 열거형에 저장함), 상태(문자열) | 예 |
| 소유자(문자열로) | 예 |
| 조회(단일 엔티티 참조 조회만) | 예 |
| 고객 | 아니요 |
| 관련 | 아니요 |
| PartyList | 아니요 |
| ManagedProperty | 아니요 |
