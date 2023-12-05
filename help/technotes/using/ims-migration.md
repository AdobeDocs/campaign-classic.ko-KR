---
title: 기술 사용자를 Adobe Developer 콘솔로 마이그레이션
description: Adobe Developer 콘솔에서 Campaign 기술 연산자를 기술 계정으로 마이그레이션하는 방법을 알아봅니다
feature: Technote
role: Admin
source-git-commit: 68d1f5ae0089a0c447acf67c28c27f4e1069a218
workflow-type: tm+mt
source-wordcount: '1646'
ht-degree: 0%

---

# Campaign 기술 운영자를 Adobe Developer 콘솔로 마이그레이션 {#migrate-tech-users-to-ims}

Campaign Classic v7.3.5부터 보안 및 인증 프로세스를 강화하기 위한 노력의 일환으로, Campaign Classic에 대한 인증 프로세스가 개선되고 있습니다. 기술 운영자는 이제 [Adobe Identity Management 시스템(IMS)](https://helpx.adobe.com/kr/enterprise/using/identity.html){target="_blank"} to connect to Campaign. Learn more about the new server to server authentication process in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}. **Adobe Campaign v7.3.5에서 이 마이그레이션을 수행하여 Campaign v8로 원활하게 마이그레이션할 수 있도록 하는 것이 좋습니다.**

기술 운영자는 API 통합을 위해 명시적으로 생성된 Campaign 사용자 프로필입니다. 이 문서에서는 Adobe Developer 콘솔을 통해 기술 연산자를 기술 계정으로 마이그레이션하는 데 필요한 단계에 대해 자세히 설명합니다.


## 영향을 받습니까?{#ims-impacts}

Campaign 외부 시스템에서 Campaign 마케팅 인스턴스 또는 실시간 메시지 센터 인스턴스로 API를 호출하는 경우, Adobe은 아래에 자세히 설명된 대로 Adobe Developer 콘솔을 통해 기술 연산자를 기술 계정으로 마이그레이션할 것을 강력히 권장합니다.

이 변경 사항은 Campaign Classic v7.3.5부터 적용할 수 있으며 **필수** Adobe Campaign v8로 이동합니다.

## 마이그레이션 프로세스 {#ims-migration-procedure}

아래 단계에 따라 Adobe Developer 콘솔 내에 기술 계정을 만든 다음 새로 만든 계정을 사용하여 Adobe Campaign에서 API를 호출하는 모든 외부 시스템에 대한 인증 방법을 변경할 수 있습니다.

단계에 대한 개요는 다음과 같습니다.

* Adobe Developer 콘솔 내에서 프로젝트 만들기
* 새로 생성된 프로젝트에 적절한 API 할당
* 프로젝트에 필요한 캠페인 제품 프로필 부여
* 새로 만든 기술 계정 자격 증명을 사용하도록 API 업데이트
* Campaign 인스턴스에서 기존 기술 연산자 제거

### 마이그레이션 사전 요구 사항{#ims-migration-prerequisites}

<!--To be able to create the technical accounts which replace the technical operators, the prerequisite that the proper Campaign Product Profiles exist within the Admin Console for all Campaign instances need to be validated. You can learn more about Product Profiles within the Adobe Console in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.-->

* Campaign Hosted 및 Managed Services 고객

  메시지 센터 인스턴스에 대한 API 호출의 경우 Campaign v7.3.5로 업그레이드하는 동안 또는 인스턴스를 프로비저닝하는 동안 제품 프로필을 만들어야 합니다. 이 제품 프로필의 이름은 다음과 같습니다.

  `campaign - <your campaign instance> - messagecenter`

  Campaign에 대한 사용자 액세스에 이미 IMS 기반 인증을 사용하고 있는 경우 API 호출에 필요한 제품 프로필이 Admin Console 내에 이미 존재해야 합니다. 마케팅 인스턴스에 대한 API 호출을 위해 Campaign 내의 사용자 지정 연산자 그룹을 사용하는 경우 Admin Console 내에 해당 제품 프로필을 만들어야 합니다.

  다른 사례의 경우, Adobe 기술 팀이 기존 운영자 Adobe 및 명명된 권한을 Admin Console 내의 제품 프로필로 마이그레이션할 수 있도록 Adobe 전환 관리자(Managed Services 사용자용) 또는 고객 지원 센터(다른 호스트형 사용자용)에 연결해야 합니다.

* Campaign On-Premise 및 하이브리드 고객

  메시지 센터 인스턴스에 대한 API 호출의 경우 이름이 인 제품 프로필을 만들어야 합니다.

  `campaign - <your campaign instance> - messagecenter`

  Campaign에 대한 사용자 액세스에 이미 IMS 기반 인증을 사용하고 있는 경우 API 호출에 필요한 제품 프로필이 Admin Console 내에 이미 존재해야 합니다. 마케팅 인스턴스에 대한 API 호출을 위해 Campaign 내의 사용자 지정 연산자 그룹을 사용하는 경우 Admin Console 내에 해당 제품 프로필을 만들어야 합니다.

  의 Adobe 콘솔에서 제품 프로필에 대해 자세히 알아볼 수 있습니다. [Adobe Developer 콘솔 설명서](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}


### 1단계 - Adobe Developer 콘솔 내에서 Campaign 프로젝트 만들기 {#ims-migration-step-1}

통합은 의 일부로 만들어집니다. **프로젝트** Adobe Developer 콘솔 내에서. 의 프로젝트에 대해 자세히 알아보기 [Adobe Developer 콘솔 설명서](https://developer.adobe.com/developer-console/docs/guides/projects/){target="_blank"}.

이전에 만든 프로젝트를 사용하거나 새 프로젝트를 만들 수 있습니다. 프로젝트를 만드는 단계는 [Adobe Developer 콘솔 설명서](https://developer.adobe.com/developer-console/docs/guides/getting-started/){target="_blank"}. 아래 주요 단계를 확인할 수 있습니다

<!--
For this migration, you must add below APIs in your project: **I/O Management API** and **Adobe Campaign**.

![](assets/do-not-localize/ims-products-and-services.png)-->

새 프로젝트를 만들려면 **새 프로젝트 만들기** Adobe Developer 콘솔의 기본 화면에서 다음을 수행합니다.

![](assets/New-Project.png)

다음을 사용할 수 있습니다. **프로젝트 편집** 단추를 클릭하여 이 프로젝트의 이름을 변경합니다.


### 2단계 - 프로젝트에 API 추가 {#ims-migration-step-2}

새로 만든 프로젝트 화면에서 이 프로젝트를 Adobe Campaign에 대한 API 호출에 대한 기술 계정으로 사용할 수 있도록 API에 를 추가합니다.

프로젝트에 API를 추가하려면 다음 단계를 수행합니다.

1. 클릭 **API 추가** 프로젝트에 추가할 API를 선택합니다.
   ![](assets/do-not-translate/ims-updates-01.png)
1. Adobe Campaign API를 선택하고 프로젝트에 추가합니다. 카드를 마우스로 가리키면 표시되는 Adobe Campaign 카드의 오른쪽 상단 모서리에 있는 상자를 선택합니다
   ![](assets/do-not-translate/ims-updates-02.png)
1. 클릭 **다음** 화면 맨 아래에.

### 3단계 - 인증 유형 선택  {#ims-migration-step-3}

다음에서 **API 구성** 화면에서 필요한 인증 유형을 선택합니다. **OAuth 서버 간** 이 프로젝트에는 인증이 필요합니다. 선택되었는지 확인하고 를 클릭합니다. **다음** 화면 맨 아래에.

![](assets/do-not-translate/ims-updates-03.png)

<!--
Once your project is created in the Adobe Developer Console, add an API that uses Server-to-Server authentication. Learn how to set up the OAuth Server-to-Server credential in [Adobe Developer Console documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/){target="_blank"}.

When the API has been successfully connected, you can access the newly generated credentials including Client ID and Client Secret, as well as generate an access token.-->

### 4단계 - 제품 프로필 선택 {#ims-migration-step-4}

전제 조건 섹션에 설명된 대로 프로젝트에서 사용할 적절한 제품 프로필을 할당해야 합니다. 이 단계에서는 생성 중인 기술 계정에서 사용할 제품 프로필을 선택해야 합니다.

이 기술 계정을 사용하여 메시지 센터 인스턴스에 대한 API를 호출하는 경우 다음으로 끝나는 제품 프로필 만들기 Adobe을 선택해야 합니다. `messagecenter`.

마케팅 인스턴스에 대한 API 호출의 경우 인스턴스 및 운영자 그룹에 해당하는 제품 프로필을 선택합니다.

필요한 제품 프로필을 선택하고 을(를) 클릭합니다. **구성된 API 저장** 화면 맨 아래에.

<!--
You can now add your Campaign product profile to the project, as detailed below:

1. Open the Adobe Campaign API.
1. Click the **Edit product profiles** button

    ![](assets/do-not-localize/ims-edit-api.png)

1. Assign all the relevant Product Profiles to the API, for example 'messagecenter', and save your changes.
1. Browse to the **Credential details** tab of your project, and copy the **Technical Account Email** value.-->

### 5단계 - 프로젝트에 I/O 관리 API 추가 {#ims-migration-step-5}


프로젝트 화면에서 **[!UICONTROL + Add to Project]** 및 선택 **[!UICONTROL API]** 화면의 왼쪽 상단에서 이 프로젝트에 I/O 관리 API를 추가할 수 있습니다.

![](assets/do-not-translate/ims-updates-04.png)

다음에서 **API 추가** 화면, 아래로 스크롤하여 **I/O 관리 API** 카드. 카드 위에 마우스를 가져다 대면 나타나는 확인란을 클릭하여 선택합니다. 그런 다음 **다음** 화면 맨 아래에.

![](assets/do-not-translate/ims-updates-05.png)


다음에서 **API 구성** 화면에 OAuth 서버 간 인증이 이미 있습니다. 클릭 **구성된 API 저장** 화면 맨 아래에.


![](assets/do-not-translate/ims-updates-06.png)

이렇게 하면 새로 생성된 프로젝트의 I/O 관리 API 내의 프로젝트 화면으로 돌아갑니다. 화면 상단의 경로에서 프로젝트 이름을 클릭하여 기본 프로젝트 세부 정보 페이지로 돌아갑니다.


### 6단계 - 프로젝트 설정 확인 {#ims-migration-step-6}

프로젝트를 검토하여 이 기능이 아래와 유사한지 확인합니다. **I/O 관리 API** 및 **ADOBE CAMPAIGN API** 제품 및 서비스 섹션에 표시되며, **OAuth 서버 간** 자격 증명 섹션에서 다음을 수행합니다.

![](assets/do-not-translate/ims-updates-07.png)


### 7단계 - 구성 유효성 검사 {#ims-migration-step-7}

연결을 시도하려면 다음에서 자세히 설명하는 단계를 수행합니다. [Adobe Developer 콘솔 자격 증명 안내서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens){target="_blank"} 액세스 토큰을 생성하고 제공된 샘플 cURL 명령을 복사합니다. 이러한 자격 증명을 사용하여 soap 호출을 만들어 Adobe Campaign 인스턴스를 올바르게 인증하고 연결할 수 있는지 테스트할 수 있습니다. 타사 API 통합을 모두 변경하기 전에 이 유효성 검사를 수행하는 것이 좋습니다.

### 8단계 - 서드파티 API 통합 업데이트 {#ims-migration-step-8}

이제 Adobe Campaign에 호출하여 새로 만든 기술 계정을 사용하려면 API 통합 을 업데이트해야 합니다.

원활한 통합을 위한 샘플 코드를 포함하여 API 통합 단계에 대한 자세한 내용은 을 참조하십시오. [Adobe Developer 콘솔 인증 설명서](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/){target="_blank"}.

다음은 타사 시스템에 대한 마이그레이션 호출 전후의 SOAP 호출 샘플을 보여 줍니다.

마이그레이션 프로세스가 달성되고 유효성이 확인되면 Soap 호출이 다음과 같이 업데이트됩니다.



* 마이그레이션 전: 기술 계정 액세스 토큰에 대한 지원이 없었습니다.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken>SESSION_TOKEN</urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```

* 마이그레이션 후: 기술 계정 액세스 토큰에 대한 지원이 있습니다. 액세스 토큰이에 다음에서 제공해야 합니다. `Authorization` 헤더를 전달자 토큰으로 사용합니다. 아래 soap 호출 샘플에 표시된 대로 여기서는 세션 토큰 사용을 무시해야 합니다.

  ```sql
  POST /nl/jsp/soaprouter.jsp HTTP/1.1
  Host: localhost:8080
  Content-Type: application/soap+xml;
  SOAPAction: "nms:rtEvent#PushEvent"
  charset=utf-8
  Authorization: Bearer <IMS_Technical_Token_Token>
  
  <?xml version="1.0" encoding="utf-8"?>  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:urn="urn:nms:rtEvent">
  <soapenv:Header/>
  <soapenv:Body>
      <urn:PushEvent>
          <urn:sessiontoken></urn:sessiontoken>
          <urn:domEvent>
              <!--You may enter ANY elements at this point-->
              <rtEvent type="type" email="name@domain.com"/>
          </urn:domEvent>
      </urn:PushEvent>
  </soapenv:Body>
  </soapenv:Envelope>
  ```



### 9단계 - (선택 사항) Campaign 클라이언트 콘솔 내에서 기술 계정 연산자 업데이트 {#ims-migration-step-9}

이 단계는 선택 사항이며 메시지 센터 인스턴스가 아닌 마케팅 인스턴스 내에서만 사용할 수 있습니다. 지정된 운영자 그룹을 통하지 않는 기술 운영자에 대해 특정 폴더 권한 또는 명명된 권한이 정의된 경우. 이제 Admin Console에서 새로 만든 기술 계정 사용자를 업데이트하여 필요한 폴더 권한 또는 명명된 권한을 부여해야 합니다.

Campaign 인스턴스에 대한 API 호출이 하나 이상 만들어져야 IMS가 Campaign 내에서 사용자를 만들 수 있으므로 기술 계정 사용자는 Adobe Campaign에 존재하지 않습니다. Campaign 내에서 기술 사용자를 찾을 수 없는 경우 설명된 대로 API 호출을 성공적으로 보낼 수 있는지 확인하십시오 [7단계](#ims-migration-step-7).

1. 새 기술 계정 사용자에게 필요한 변경 사항을 적용하려면 Campaign 클라이언트 콘솔 내에서 이메일 주소로 해당 변경 사항을 찾습니다. 이 이메일 주소는 위의 프로젝트 만들기 및 인증 단계 동안 만들어졌습니다.

   다음을 클릭하여 이 이메일 주소를 찾을 수 있습니다. **OAuth 서버 간** 제목 **자격 증명** 섹션에 있는 마지막 항목이 될 필요가 없습니다.

   ![](assets/do-not-translate/ims-updates-07.png)

   자격 증명 화면에서 아래로 스크롤하여 **기술 계정 이메일**을 찾고 **복사** 단추를 클릭합니다.

   ![](assets/do-not-translate/ims-updates-08.png)

1. 이제 Adobe Campaign 클라이언트 콘솔에서 새로 만든 기술 연산자를 업데이트해야 합니다. 기존 기술 운영자 폴더 권한을 새 기술 운영자에게 적용해야 합니다.

   이 연산자를 업데이트하려면 다음 단계를 수행합니다.

   1. Campaign 클라이언트 콘솔 탐색기에서 **관리 > 액세스 관리 > 연산자**.
   1. API에 사용되는 기존 기술 운영자에 액세스합니다.
   1. 폴더 권한을 찾아 권한을 확인합니다.
   1. 새로 만든 기술 운영자에게 동일한 권한을 적용합니다. 이 운영자의 이메일은 **기술 계정 이메일** 값이 이전에 복사되었습니다.
   1. 변경 내용을 저장합니다.


>[!CAUTION]
>
>새 기술 운영자가 Campaign 클라이언트 콘솔에 추가할 API 호출을 하나 이상 수행해야 합니다.
>

### 10단계 - Adobe Campaign에서 이전 기술 연산자 제거 {#ims-migration-step-10}

모든 타사 시스템을 마이그레이션하여 IMS 인증이 있는 새 기술 계정을 사용하면 Campaign 클라이언트 콘솔에서 이전 기술 연산자를 삭제할 수 있습니다.

이렇게 하려면 Campaign 클라이언트 콘솔에 로그인하고 로 이동합니다. **관리 > 액세스 관리 > 연산자** 이전 기술 사용자를 찾아 삭제합니다.
