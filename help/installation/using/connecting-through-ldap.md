---
product: campaign
title: LDAP를 통해 연결
description: LDAP를 사용하여 Campaign에 로그인하는 방법 알아보기
feature: Installation, Instance Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 0533cd50-3aa4-4160-9152-e916e149e77f
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 0%

---

# LDAP를 통해 연결 {#connecting-through-ldap}

## Campaign 및 LDAP 구성 {#configuring-campaign-and-ldap}

>[!NOTE]
>
>* LDAP 구성은 온-프레미스 또는 하이브리드 설치에서만 가능합니다.
>
>* 시스템 및 openssl 버전이 [호환성 매트릭스](../../rn/using/compatibility-matrix.md)에서 Campaign과 호환되는지 확인하십시오. 오래된 버전은 LDAP 인증에 영향을 줄 수 있습니다.
>

LDAP 구성은 배포 마법사에서 수행됩니다. 첫 번째 구성 단계에서 **[!UICONTROL LDAP integration]** 옵션을 선택해야 합니다. [배포 마법사](../../installation/using/deploying-an-instance.md#deployment-assistant)를 참조하세요.

이 창에서는 지정된 LDAP 디렉터리를 통해 Adobe Campaign 사용자 식별을 구성할 수 있습니다.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* **[!UICONTROL LDAP server]** 필드에 LDAP 서버의 주소를 지정하십시오. 포트 번호를 추가할 수 있습니다. 기본적으로 사용되는 포트는 389입니다.
* 드롭다운 목록에서 사용자에 대한 인증 방법을 선택합니다.

   * 암호화된 암호(**md5**) - 기본 모드입니다.

   * 일반 텍스트 암호 + SSL(**TLS**) - 전체 인증 절차(암호 포함)가 암호화됩니다. 이 모드에서는 보안 포트 636을 사용하지 않아야 합니다. Adobe Campaign은 자동으로 보안 모드로 전환됩니다.

     이 인증 모드를 사용하는 경우 Linux에서는 openLDAP 클라이언트 라이브러리로 인증서를 확인합니다. 인증 절차가 암호화되도록 유효한 SSL 인증서를 사용하는 것이 좋습니다. 그렇지 않으면 정보는 일반 텍스트로 표시됩니다.

     인증서는 Windows에서도 확인됩니다.

   * Windows NT LAN 관리자(**NTLM**) - 소유 Windows 인증. **[!UICONTROL Unique identifier]**&#x200B;은(는) 도메인 이름에만 사용됩니다.

   * 분산 암호 인증(**DPA**) - 전용 Windows 인증. **[!UICONTROL Unique identifier]**&#x200B;은(는) 도메인 이름(domain.com)에만 사용됩니다.

   * 일반 텍스트 암호 - 암호화 없음(테스트 단계에서만 사용).

* 사용자 인증 모드를 선택하십시오. **[!UICONTROL Automatically compute the unique user identifier]**([고유 이름 계산](#distinguished-name-calculation)단계 참조) 또는 **[!UICONTROL Search the unique user identifier in the directory]**([식별자 검색](#searching-for-identifiers)단계 참조).

## 호환성 {#compatibility}

호환되는 시스템은 선택한 인증 메커니즘에 따라 다릅니다. 다음은 운영 체제와 LDAP 서버의 호환성 매트릭스입니다.

<table> 
 <thead> 
  <tr> 
   <th> </th> 
   <th> OpenLDAP<br /> </th> 
   <th> Active Directory<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> md5<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> TLS<br /> </td> 
   <td> Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
  <tr> 
   <td> NTLM 및 DPA<br /> </td> 
   <td> </td> 
   <td> Windows<br /> </td> 
  </tr> 
  <tr> 
   <td> 일반 텍스트<br /> </td> 
   <td> Windows, Linux<br /> </td> 
   <td> Windows, Linux<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 고유 이름 계산 {#distinguished-name-calculation}

DN(식별 이름) 식별자를 계산하려는 경우 배포 마법사의 다음 단계에서 계산 모드를 구성할 수 있습니다.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* **[!UICONTROL Distinguished Name]** 필드의 디렉터리(고유 이름 - DN)에서 사용자의 고유 식별자를 지정합니다.

  **[!UICONTROL (login)]**&#x200B;은(는) Adobe Campaign 연산자의 식별자로 대체됩니다.

  >[!CAUTION]
  >
  >**[!UICONTROL dc]** 설정은 소문자여야 합니다.

* LDAP 디렉터리의 그룹 및 사용자 연결과 Adobe Campaign의 그룹 및 사용자 연결을 동기화하려면 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 선택하십시오.

  이 옵션을 선택하면 **[!UICONTROL Application level DN used for the search]** 및 **[!UICONTROL Password of the application login]**&#x200B;이(가) 활성화됩니다.

  이 두 필드를 채우면 Adobe Campaign이 자체 로그인 및 암호로 LDAP 서버에 연결됩니다. 비어 있는 경우 Adobe Campaign이 익명으로 서버에 연결됩니다.

## 식별자 검색 {#searching-for-identifiers}

식별자를 검색하도록 선택하는 경우 배포 마법사를 사용하여 검색을 구성할 수 있습니다.

* **[!UICONTROL Application level DN used for the search]** 및 **[!UICONTROL Password of the application login]** 필드에 Adobe Campaign에서 식별자를 검색하기 위해 연결할 식별자와 암호를 입력합니다. 비어 있는 경우 Adobe Campaign이 익명으로 서버에 연결됩니다.
* 검색을 시작할 LDAP 디렉터리의 하위 집합을 결정하려면 **[!UICONTROL Base identifier]** 및 **[!UICONTROL Search scope]** 필드를 지정하십시오.

  드롭다운 목록에서 필요한 모드를 선택합니다.

  ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      LDAP 디렉터리는 지정된 수준부터 전체 검색됩니다.

   1. **[!UICONTROL Limited to the base]**.

      모든 속성은 검색에 포함됩니다.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      검색은 디렉토리의 모든 속성에 대해 수행되며 속성의 첫 번째 레벨에서 시작됩니다.

* **[!UICONTROL Filter]** 필드를 사용하면 검색 범위를 구체화할 요소를 지정할 수 있습니다.

## LDAP 권한 구성 {#configuring-ldap-authorizations}

**[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 선택하면 이 창이 표시됩니다.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

사용자가 속한 그룹 및 해당 권한을 찾으려면 여러 매개 변수를 지정해야 합니다(예:

* **[!UICONTROL Database identifier]** 필드,
* **[!UICONTROL Search scope]** 필드,

  >[!NOTE]
  >
  >DN을 검색하도록 선택한 경우 **[!UICONTROL Reuse the DN search parameters]**&#x200B;을(를) 선택하여 이전 화면에서 DN 및 검색 범위에 대해 선택한 값을 전달할 수 있습니다.

* 로그인 및 사용자의 고유 이름을 기반으로 하는 **[!UICONTROL Rights search filter]** 필드
* 사용자에 대한 **[!UICONTROL Attribute containing the group or authorization name]** 필드,
* Adobe Campaign에서 그룹 이름 및 관련 권한을 추출할 수 있는 **[!UICONTROL Association mask]** 필드. 정규 표현식을 사용하여 이름을 검색할 수 있습니다.
* **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]**&#x200B;을(를) 선택하여 사용자에게 연결에 대한 액세스 권한이 자동으로 부여되도록 합니다.

인스턴스 구성을 완료하려면 **[!UICONTROL Save]**&#x200B;을(를) 클릭하십시오.

## 운영자 관리 {#managing-operators}

구성을 확인했으면 LDAP 디렉터리를 통해 관리되는 Adobe Campaign 연산자를 정의해야 합니다.

LDAP 디렉터리를 사용하여 연산자를 인증하려면 해당 프로필을 편집하고 **[!UICONTROL Edit the access parameters]** 링크를 클릭합니다. **[!UICONTROL Use LDAP for authentication]** 옵션을 선택하십시오. 이 연산자에 대해 **[!UICONTROL Password]** 필드가 회색으로 표시됩니다.

![](assets/s_ncs_install_operator_in_ldap.png)

## 활용 사례 {#use-cases}

이 섹션에서는 필요에 따라 가장 적절한 구성을 수행하는 데 도움이 되는 몇 가지 간단한 사용 사례를 제공합니다.

1. LDAP 디렉터리에 사용자가 생성되었지만 Adobe Campaign에는 없습니다.

   사용자가 LDAP 인증을 통해 플랫폼에 액세스하도록 Adobe Campaign을 구성할 수 있습니다. Adobe CampaignAdobe Campaign 에서 즉시 연산자를 만들 수 있도록 LDAP 디렉터리에서 ID/암호 조합의 유효성을 제어할 수 있어야 합니다. 이렇게 하려면 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 옵션을 선택하십시오. 이 경우 그룹 동기화도 구성해야 합니다. **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 선택해야 합니다.

1. 사용자가 Adobe Campaign에서 생성되었지만 LDAP 디렉터리에서는 생성되지 않았습니다.

   Adobe Campaign에 로그온할 수 없습니다.

1. LDAP 디렉터리에 Adobe Campaign에 없는 그룹이 있습니다.

   이 그룹은 Adobe Campaign에서 생성되지 않습니다. **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 통해 일치를 사용하려면 그룹을 만들고 동기화해야 합니다.

1. 그룹이 Adobe Campaign에 있고 이벤트 후 LDAP 디렉터리가 활성화됩니다. Adobe Campaign의 사용자 그룹은 자동으로 LDAP 그룹의 콘텐츠로 대체되지 않습니다. 마찬가지로, 그룹이 Adobe Campaign에만 있는 경우 LDAP에서 그룹을 만들고 동기화할 때까지 LDAP 사용자를 추가할 수 없습니다.

   그룹은 Adobe Campaign 또는 LDAP에 의해 즉시 만들어지지 않습니다. Adobe Campaign 및 LDAP 디렉터리 모두에서 개별적으로 만들어야 합니다.

   LDAP 디렉토리의 그룹 이름은 Adobe Campaign 그룹의 이름과 일치해야 합니다. 연결 마스크는 배포 마법사의 마지막 구성 단계인 Adobe Campaign_()에서 정의됩니다.예를 들어 &#42;)입니다.
