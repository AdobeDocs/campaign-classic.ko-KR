---
product: campaign
title: Campaign 운영자 시작
description: Campaign 사용자를 만들고 관리하는 방법을 알아봅니다
feature: Access Management
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 2%

---

# 운영자 만들기 및 관리 {#operators}

![](../../assets/common.svg)

## Campaign 운영자 시작  {#about-operators}

연산자는 로그인 및 작업을 수행할 수 있는 권한이 있는 Adobe Campaign 사용자입니다.

기본적으로 연산자는 **[!UICONTROL Administration > Access management > Operators]** 노드에 저장됩니다.

![](assets/s_ncs_user_list_operators.png)

연산자를 수동으로 만들거나 기존 LDAP 디렉토리에 매핑할 수 있습니다.

연산자를 만드는 전체 프로시저는 [이 페이지](#creating-an-operator)에 설명되어 있습니다.

Adobe Campaign 및 LDAP 통합에 대한 자세한 내용은 [이 페이지](../../installation/using/connecting-through-ldap.md)를 참조하십시오.

>[!IMPORTANT]
>
>인스턴스에 로그온하려면 연산자를 보안 영역에 연결해야 합니다. Adobe Campaign의 보안 영역에 대한 자세한 내용은 [이 페이지](../../installation/using/security-zones.md)를 참조하십시오.

사용자는 Adobe ID을 사용하여 Adobe Campaign에 직접 연결할 수도 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

## 연산자 만들기 {#creating-an-operator}

새 연산자를 만들고 권한을 부여하려면 아래 단계를 수행하십시오.

1. 연산자 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭하고 새 연산자의 세부 정보를 입력합니다.

   ![](assets/s_ncs_user_operator_new.png)

1. 사용자의 **[!UICONTROL Identification parameters]** 지정: 로그인, 암호 및 이름입니다. 연산자가 Adobe Campaign에 로그온하는 데 로그인 및 암호를 사용합니다. 사용자가 로그온하면 **[!UICONTROL Tools > Change password]** 메뉴를 통해 암호를 변경할 수 있습니다. 예를 들어 승인 처리 시 연산자가 알림을 받을 수 있으므로 연산자의 이메일이 필수입니다.

   또한 이 섹션에서는 연산자를 조직 엔터티에 연결할 수도 있습니다. 자세한 내용은 [이 페이지](../../distributed/using/about-distributed-marketing.md)를 참조하십시오.

1. **[!UICONTROL Operator access rights]** 섹션에서 연산자에 부여된 권한을 선택합니다.

   연산자에 권한을 할당하려면 권한 목록 위에 있는 **[!UICONTROL Add]** 단추를 클릭한 다음 사용 가능한 그룹 목록에서 연산자 그룹을 선택합니다.

   ![](assets/s_ncs_user_permissions_operators.png)

   명명된 권한을 하나 이상 선택할 수도 있습니다( [명명된 권한](#named-rights) 참조). 이렇게 하려면 **[!UICONTROL Folder]** 필드 오른쪽의 화살표를 클릭하고 **[!UICONTROL Named rights]** 을 선택합니다.

   ![](assets/s_ncs_user_rights_operators.png)

   할당할 그룹 및/또는 명명된 권한을 선택하고 **[!UICONTROL OK]** 을 클릭하여 유효성을 확인합니다.

1. **[!UICONTROL Ok]** 을 클릭하여 연산자를 만듭니다. 기존 연산자 목록에 프로필이 추가됩니다.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>새 운영자 폴더를 만들어 필요에 따라 연산자를 구성할 수 있습니다. 이렇게 하려면 연산자 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Add an 'Operators' folder]** 을 선택합니다.

연산자의 프로필이 만들어지면 해당 정보에 을 추가하거나 업데이트할 수 있습니다. 이렇게 하려면 **[!UICONTROL Edit]** 탭을 클릭합니다.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>**[!UICONTROL Session timeout]** 필드를 사용하면 FDA 세션 시간 초과 전에 지연을 조정할 수 있습니다. 자세한 내용은 [페더레이션 데이터 액세스 정보](../../installation/using/about-fda.md)를 참조하십시오.

## 연산자의 시간대를 정의합니다. {#time-zone-of-the-operator}

**[!UICONTROL General]** 탭에서 연산자의 시간대를 선택할 수 있습니다. 기본적으로 연산자는 서버 시간대에서 작동합니다. 그러나 드롭다운 목록을 사용하여 다른 시간대를 선택할 수 있습니다.

시간대의 구성은 [이 페이지](../../installation/using/time-zone-management.md)에 설명되어 있습니다.

>[!NOTE]
>
>다양한 시간대 내의 공동 작업은 UTC로 날짜를 저장해야 합니다. 날짜는 다음 컨텍스트의 해당 시간대에서 변환됩니다. 사용자 시간대에 날짜가 표시되면 파일을 가져오고 내보낼 때 이메일 게재를 예약할 때 워크플로우에서 활동이 예약되는 시간(스케줄러, 대기, 시간 제한 등)
>
>이러한 컨텍스트에 연결된 제한 및 권장 사항은 Adobe Campaign 설명서의 관련 섹션에 나와 있습니다.

또한 **[!UICONTROL Regional settings]** 드롭다운 목록에서 날짜 및 숫자를 표시할 형식을 선택할 수 있습니다.

## 권한 추가 {#access-rights-options}

**[!UICONTROL Access rights]** 탭을 사용하여 연산자에 연결된 그룹 및 명명된 권한을 업데이트합니다.

![](assets/operator_profile_security_options.png)

**[!UICONTROL Edit the access parameters...]** 링크를 통해 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL Disable account]** 옵션을 사용하면 연산자의 계정을 비활성화할 수 있습니다. 더 이상 Adobe Campaign에 액세스할 수 없습니다.

   >[!NOTE]
   >
   >계정이 비활성화되었더라도 운영자가 Campaign에서 경고나 알림을 계속 받을 수 있습니다. 이 운영자에게 Campaign 알림 전송을 중단하려면 Adobe에서 이 프로필에서 이메일 주소를 제거하는 것이 좋습니다.

* **[!UICONTROL Forbid access from the rich client]** 옵션을 사용하면 Adobe Campaign을 [웹 액세스](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 또는 API를 통해 사용하도록 제한할 수 있습니다. Adobe Campaign 클라이언트 콘솔에 대한 액세스를 더 이상 사용할 수 없습니다.
* 작동자에게 안전구역을 연결할 수 있습니다 자세한 정보는 이 [페이지](../../installation/using/security-zones.md)를 참조하십시오.
* 적절한 링크를 사용하여 신뢰할 수 있는 IP 마스크를 정의할 수도 있습니다.

   연산자는 IP 주소가 이 목록에 있는 경우 암호를 입력하지 않고 Adobe Campaign에 연결할 수 있습니다.

   다음 예와 같이 암호 없이 연결할 수 있는 권한을 부여할 IP 주소 집합을 지정할 수도 있습니다.

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >플랫폼에 안전하게 액세스하려면 이 옵션을 신중하게 사용해야 합니다.

* **[!UICONTROL Restrict to information found in sub-folders of:]** 옵션을 사용하면 폴더 연산자에 속하는 권한을 제한할 수 있습니다. 이 옵션에 지정된 노드의 하위 폴더만 사용자에게 표시됩니다.

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >이것은 매우 엄격한 제한이므로 주의해서 사용해야 한다. 이 유형의 권한으로 로그인한 연산자는 지정된 폴더의 컨텐츠만 볼 수 있으며 탐색기를 통해 트리의 다른 노드에 액세스할 수 없습니다. 그러나 액세스 권한이 있는 기능에 따라(예: 워크플로우)를 채울 수 있으며 일반적으로 볼 수 없는 노드에 저장된 데이터를 표시할 수 있습니다.

### 설정 확인 {#check-settings}

**[!UICONTROL Audit]** 탭에서는 연산자와 관련된 정보를 볼 수 있습니다. 연산자의 개입 영역에 정의된 설정에 따라 다양한 탭이 자동으로 에 추가됩니다.

다음 항목에 액세스할 수 있습니다.

* 연산자에 연결된 폴더에 대한 권한 목록입니다.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >자세한 내용은 [폴더 액세스 관리](#folder-access-management)를 참조하십시오.

* 운영자 승인 로그입니다.

   ![](assets/operator_profile_validations.png)

* 구독한 토론 포럼 목록입니다.
* 달력 내 이벤트.
* 할당된 작업 목록입니다.

## 기본 연산자 {#default-operators}

Adobe Campaign은 기본적으로 구성된 프로필과 함께 기술 운영자를 사용합니다. 관리자(&#39;admin&#39;), 청구(&#39;billing&#39;), 모니터링, 웹 애플리케이션 에이전트(&#39;webapp&#39;) 등 이러한 옵션 중 일부는 플랫폼에 설치된 애플리케이션 및 옵션에 따라 다릅니다. 예를 들어 &#39;central&#39; 및 &#39;local&#39; 연산자는 분산 마케팅 옵션이 설치된 경우에만 표시됩니다.

>[!IMPORTANT]
>
>이러한 기술 운영자는 플랫폼에서 정보 메시지를 반환하면 기본적으로 알림을 받습니다. 이들에게 이메일을 보내는 것이 좋습니다.
>
>웹 응용 프로그램이 올바르게 작동하도록 하려면 &#39;webapp&#39; 연산자에 대한 특정 지역 설정을 정의하지 않는 것이 좋습니다.

기본적으로 &#39;webapp&#39; 기술 운영자에게는 명명된 ADMINISTRATION 권한이 있으며 이로 인해 보안 위험이 발생할 수 있습니다. 이 문제를 해결하려면 이 권한을 제거하는 것이 좋습니다. 방법은 다음과 같습니다.

1. **[!UICONTROL Administration > Access management > Named rights]** 노드에서 **[!UICONTROL New]** 를 클릭하여 권한을 만들고 이름을 WEBAPP로 지정합니다.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   명명된 권한은 [명명된 권한](#named-rights) 섹션에 자세히 설명되어 있습니다.

1. **[!UICONTROL Administration > Access management > Operators]** 노드에서 웹 응용 프로그램 에이전트 연산자(&#39;webapp&#39;)를 선택합니다.

   **[!UICONTROL Edit]** 탭을 선택한 다음 **[!UICONTROL Access rights]** 탭을 선택하고 목록에서 바로 이름이 지정된 ADMINISTRATION을 삭제합니다.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   **[!UICONTROL Add]** 을 클릭하고 방금 만든 WEBAPP 권한을 선택한 다음 변경 사항을 저장합니다.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 주로 &#39;받는 사람&#39; 폴더인 이 연산자와 관련된 폴더에 대해 &#39;webapp&#39; 연산자를 읽고 쓰기 데이터 액세스 권한을 할당합니다.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   트리 폴더의 권한 수정은 [폴더 액세스 관리](#folder-access-management) 섹션에 자세히 설명되어 있습니다.

>[!NOTE]
>
>보안 지침에 대한 자세한 내용은 [Adobe Campaign 보안 구성 검사 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)을 참조하십시오.
