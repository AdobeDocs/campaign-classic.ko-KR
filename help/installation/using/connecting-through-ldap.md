---
title: LDAP를 통해 연결
seo-title: LDAP를 통해 연결
description: LDAP를 통해 연결
seo-description: null
page-status-flag: never-activated
uuid: 13a426bc-7c34-49e5-ac8e-26d830845f28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1563db7c-ccb6-46b3-9299-67ec0aedaca0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# LDAP를 통해 연결{#connecting-through-ldap}

## 캠페인 및 LDAP 구성 {#configuring-campaign-and-ldap}

>[!NOTE]
>
>LDAP 구성은 온-프레미스 또는 하이브리드 설치에만 가능합니다.

LDAP 구성은 배포 마법사에서 수행됩니다. 첫 번째 구성 단계에서 옵션을 선택해야 **[!UICONTROL LDAP integration]** 합니다. 배포 [마법사를](../../installation/using/deploying-an-instance.md#deployment-wizard)참조하십시오.

이 창에서 지정된 LDAP 디렉토리를 통해 Adobe Campaign 사용자의 ID를 구성할 수 있습니다.

![](assets/s_ncs_install_deployment_wiz_ldap_01.png)

* 필드에 LDAP 서버의 주소를 **[!UICONTROL LDAP server]** 지정합니다. 포트 번호를 추가할 수 있습니다. 기본적으로 사용된 포트는 389입니다.
* 드롭다운 목록에서 사용자에 대한 인증 방법을 선택합니다.

   * 암호화된 암호(**md5**)

      기본 모드.

   * 일반 텍스트 암호 + SSL(**TLS**)

      전체 인증 절차(암호 포함)가 암호화됩니다. 이 모드에서는 보안 포트 636을 사용할 수 없습니다.Adobe Campaign은 자동으로 보안 모드로 전환됩니다.

      Linux에서 이 인증 모드를 사용하면 열린 LDAP 클라이언트 라이브러리에서 인증서를 확인합니다. 인증 절차가 암호화되도록 유효한 SSL 인증서를 사용하는 것이 좋습니다. 그렇지 않으면 정보가 일반 텍스트로 표시됩니다.

      인증서는 Windows에서도 확인됩니다.

   * Windows NT LAN Manager(**NTLM**)

      전용 Windows 인증. 은 도메인 **[!UICONTROL Unique identifier]** 이름에만 사용됩니다.

   * DPA(Distributed Password **Authentication**)

      전용 Windows 인증. 은 도메인 **[!UICONTROL Unique identifier]** 이름에만 사용됩니다(domain.com).

   * 일반 텍스트 암호

      암호화 없음(테스트 단계에서만 사용).

* 사용자 인증 모드를 선택합니다.단계 고유 **[!UICONTROL Automatically compute the unique user identifier]** 이름 계산 [참조) 또는](#distinguished-name-calculation)(식별자 **[!UICONTROL Search the unique user identifier in the directory]** 검색 단계 [참조](#searching-for-identifiers))

## 호환성 {#compatibility}

호환되는 시스템은 선택한 인증 메커니즘에 따라 다릅니다. 다음은 운영 체제 및 LDAP 서버의 호환성 매트릭스입니다.

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

DN(고유 이름) 식별자를 계산하려는 경우 배포 마법사의 다음 단계에서 계산 모드를 구성할 수 있습니다.

![](assets/s_ncs_install_deployment_wiz_ldap_02.png)

* 필드의 디렉토리(고유 이름 - DN)에서 사용자의 고유 식별자를 지정합니다 **[!UICONTROL Distinguished Name]** .

   **[!UICONTROL (login)]** 이 Adobe Campaign 연산자의 식별자로 대체됩니다.

   >[!CAUTION]
   >
   >설정은 **[!UICONTROL dc]** 소문자여야 합니다.

* LDAP 디렉토리에서 그룹 및 사용자 연결을 동기화하고 Adobe Campaign **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 의 그룹 및 사용자 연결을 동기화하려면 옵션을 선택합니다.

   이 옵션을 선택하면 **[!UICONTROL Application level DN used for the search]** 및 **[!UICONTROL Password of the application login]** 가 활성화됩니다.

   이 두 필드를 채우면 Adobe Campaign은 자체 로그인 및 암호를 사용하여 LDAP 서버에 연결됩니다. 비어 있는 경우 Adobe Campaign은 익명으로 서버에 연결됩니다.

## 식별자 검색 {#searching-for-identifiers}

식별자를 검색하도록 선택하는 경우 배포 마법사를 사용하여 검색을 구성할 수 있습니다.

* 및 **[!UICONTROL Application level DN used for the search]** **[!UICONTROL Password of the application login]** 필드에서 Adobe Campaign이 식별자를 검색하기 위해 연결할 식별자 및 암호를 제공합니다. 비어 있는 경우 Adobe Campaign은 익명으로 서버에 연결됩니다.
* 검색을 시작할 LDAP 디렉토리의 하위 집합을 결정하려면 **[!UICONTROL Base identifier]** 및 **[!UICONTROL Search scope]** 필드를 지정합니다.

   드롭다운 목록에서 필요한 모드를 선택합니다.

   ![](assets/s_ncs_install_deployment_wiz_ldap_03.png)

   1. **[!UICONTROL Recursive (default mode)]**.

      LDAP 디렉토리는 지정된 수준에서 시작하여 전체 항목으로 검색됩니다.

   1. **[!UICONTROL Limited to the base]**.

      모든 속성이 검색에 포함됩니다.

   1. **[!UICONTROL Limited to the first sub-level of the base]**.

      디렉토리의 모든 속성에 대해 검색이 수행되고 속성의 첫 번째 레벨부터 시작됩니다.

* 이 **[!UICONTROL Filter]** 필드를 사용하면 검색 범위를 조정할 요소를 지정할 수 있습니다.

## LDAP 인증 구성 {#configuring-ldap-authorizations}

이 창은 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 선택하면 표시됩니다.

![](assets/s_ncs_install_deployment_wiz_ldap_04.png)

사용자가 속한 그룹 또는 그룹과 해당 권한(예:

* 현장 **[!UICONTROL Database identifier]** ,
* 현장 **[!UICONTROL Search scope]** ,

   >[!NOTE]
   >
   >DN을 검색하도록 선택한 경우, DN에 대해 선택한 값과 이전 화면에서 검색 범위를 **[!UICONTROL Reuse the DN search parameters]** 이월하기 위해 선택할 수 있습니다.

* 로그인 및 사용자의 고유 이름을 기반으로 하는 **[!UICONTROL Rights search filter]** 필드
* 사용자와 관련된 **[!UICONTROL Attribute containing the group or authorization name]** 필드,
* adobe Campaign에서 그룹 이름을 추출할 수 있는 **[!UICONTROL Association mask]** 필드 및 관련 권한 정규 표현식을 사용하여 이름을 검색할 수 있습니다.
* 사용자가 연결에 대한 액세스 권한이 자동으로 부여되도록 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 선택합니다.

을 **[!UICONTROL Save]** 클릭하여 인스턴스 구성을 마칩니다.

## 관리 연산자 {#managing-operators}

구성을 확인했으면 LDAP 디렉토리를 통해 관리되는 Adobe Campaign 연산자를 정의해야 합니다.

LDAP 디렉토리를 사용하여 연산자를 인증하려면 해당 프로파일을 편집하고 **[!UICONTROL Edit the access parameters]** 링크를 클릭합니다. 다음 **[!UICONTROL Use LDAP for authentication]** 옵션을 선택합니다.이 **[!UICONTROL Password]** 연산자에 대해 필드가 회색으로 표시됩니다.

![](assets/s_ncs_install_operator_in_ldap.png)

## 활용 사례 {#use-cases}

이 섹션에서는 요구 사항에 따라 가장 적합한 구성을 얻는 데 도움이 되는 몇 가지 간단한 사용 사례를 제공합니다.

1. 사용자가 LDAP 디렉토리에 만들어졌지만 Adobe Campaign에는 만들어지지 않았습니다.

   사용자가 LDAP 인증을 통해 플랫폼에 액세스할 수 있도록 Adobe Campaign을 구성할 수 있습니다. Adobe Campaign에서 연산자를 즉시 만들 수 있도록 LDAP 디렉토리에서 ID/암호 조합의 유효성을 제어할 수 있어야 합니다. 이렇게 하려면 **[!UICONTROL Enable the connection of users declared in the LDAP directory if the operator is not declared in Adobe Campaign]** 옵션을 선택합니다. 이 경우 그룹 동기화를 구성해야 합니다.이 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 선택해야 합니다.

1. 사용자가 Adobe Campaign에서 만들어졌지만 LDAP 디렉토리에서는 만들어지지 않았습니다.

   Adobe Campaign에 로그인할 수 없습니다.

1. LDAP 디렉토리에 Adobe Campaign에 존재하지 않는 그룹이 있습니다.

   이 그룹은 Adobe Campaign에서 생성되지 않습니다. 이 **[!UICONTROL Enable synchronization of user rights from authorizations and groups in the directory]** 옵션을 통해 일치를 활성화하려면 그룹을 만들고 그룹을 동기화해야 합니다.

1. 그룹은 Adobe Campaign에 존재하며, 이벤트 후 LDAP 디렉토리가 활성화됩니다.adobe Campaign의 사용자 그룹은 LDAP 그룹의 컨텐츠로 자동 대체되지 않습니다. 마찬가지로, 그룹이 Adobe Campaign에만 존재하는 경우, LDAP에서 그룹을 만들고 동기화할 때까지 LDAP 사용자를 추가할 수 없습니다.

   그룹은 Adobe Campaign 또는 LDAP에 의해 즉시 만들어지지 않습니다. Adobe Campaign과 LDAP 디렉토리 모두에서 개별적으로 만들어야 합니다.

   LDAP 디렉토리의 그룹 이름은 Adobe Campaign 그룹의 이름과 일치해야 합니다. 연결 마스크는 배포 마법사의 마지막 구성 단계에서 정의됩니다.Adobe Campaign_(.*).

