---
product: campaign
title: Campaign 연산자 시작
description: 캠페인 사용자를 만들고 관리하는 방법 알아보기
badge: label="v7" type="Informative" tooltip="Campaign Classic v7에만 적용"
feature: Access Management, Permissions
role: User, Admin
level: Beginner
exl-id: 580282ce-ee30-422a-8724-9c328637cc39
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 2%

---

# 운영자 만들기 및 관리 {#operators}



## Campaign 연산자 시작  {#about-operators}

운영자는 로그인하고 작업을 수행할 수 있는 권한이 있는 Adobe Campaign 사용자입니다.

기본적으로 연산자는 **[!UICONTROL Administration > Access management > Operators]** 노드.

![](assets/s_ncs_user_list_operators.png)

연산자는 수동으로 생성하거나 기존 LDAP 디렉토리에 매핑할 수 있습니다.

연산자를 만드는 전체 절차는에 설명되어 있습니다 [이 페이지](#creating-an-operator).

Adobe Campaign 및 LDAP 통합에 대한 자세한 내용은 [이 페이지](../../installation/using/connecting-through-ldap.md).

>[!IMPORTANT]
>
>운영자가 인스턴스에 로그온하려면 보안 영역에 연결되어 있어야 합니다. Adobe Campaign의 보안 영역에 대한 자세한 내용은 [이 페이지](../../installation/using/security-zones.md).

사용자는 Adobe ID을 사용하여 Adobe Campaign에 직접 연결할 수도 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

## 연산자 만들기 {#creating-an-operator}

새 연산자를 만들고 권한을 부여하려면 아래 단계를 수행합니다.

1. 다음을 클릭합니다. **[!UICONTROL New]** 연산자 목록 위에 있는 단추를 누르고 새 연산자의 세부 정보를 입력합니다.

   ![](assets/s_ncs_user_operator_new.png)

1. 다음을 지정합니다. **[!UICONTROL Identification parameters]** 사용자: 로그인, 암호 및 이름. 운영자는 로그인 및 암호를 사용하여 Adobe Campaign에 로그온합니다. 사용자가 로그인한 후 다음을 통해 암호를 변경할 수 있습니다. **[!UICONTROL Tools > Change password]** 메뉴 아래의 제품에서 사용할 수 있습니다. 운영자의 이메일은 운영자가 예를 들어 승인을 처리할 때 알림을 받을 수 있도록 하기 때문에 필수적입니다.

   또한 이 섹션에서는 연산자를 조직 엔티티에 연결할 수도 있습니다. 자세한 내용은 [이 페이지](../../distributed/using/about-distributed-marketing.md).

1. 에서 연산자에게 부여된 권한을 선택합니다. **[!UICONTROL Operator access rights]** 섹션.

   연산자에 권한을 할당하려면 **[!UICONTROL Add]** 권한 목록 위에 있는 단추를 누르면 사용 가능한 그룹 목록에서 연산자 그룹을 선택합니다.

   ![](assets/s_ncs_user_permissions_operators.png)

   하나 이상의 명명된 권한을 선택할 수도 있습니다( 참조) [명명된 권한](#named-rights)). 이렇게 하려면 오른쪽 화살표를 클릭합니다. **[!UICONTROL Folder]** 필드 및 선택 **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   할당할 그룹 및/또는 명명된 권한을 선택하고 **[!UICONTROL OK]** 유효성을 검사합니다.

1. 클릭 **[!UICONTROL Ok]** 연산자를 만들려면: 프로필이 기존 연산자 목록에 추가됩니다.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>새 연산자 폴더를 만들어 요구 사항에 따라 연산자를 구성할 수 있습니다. 이렇게 하려면 연산자 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Add an 'Operators' folder]**.

운영자 프로필이 생성되면 해당 정보를 추가하거나 업데이트할 수 있습니다. 이렇게 하려면 **[!UICONTROL Edit]** 탭.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>다음 **[!UICONTROL Session timeout]** 필드를 사용하면 FDA 세션 시간 초과 전에 지연을 조정할 수 있습니다. 자세한 내용은 다음을 참조하십시오. [Federated Data Access 정보](../../installation/using/about-fda.md).

## 연산자의 시간대 정의 {#time-zone-of-the-operator}

다음에서 **[!UICONTROL General]** 탭에서 연산자의 시간대를 선택할 수 있습니다. 기본적으로 운영자는 서버 시간대에서 작업합니다. 그러나 드롭다운 목록을 사용하여 다른 시간대를 선택할 수 있습니다.

시간대의 구성은에 설명되어 있습니다 [이 페이지](../../installation/using/time-zone-management.md).

>[!NOTE]
>
>다양한 시간대 내의 공동 작업에는 날짜를 UTC로 저장해야 합니다. 날짜가 사용자 시간대에 표시되는 경우, 파일을 가져오고 내보내는 경우, 이메일 배달이 예약되는 경우, 워크플로우에서 활동이 예약되는 경우(스케줄러, 대기, 시간 제한 등) 등 컨텍스트에서 날짜는 적절한 시간대로 변환됩니다.
>
>이러한 컨텍스트와 연결된 제한 및 권장 사항은 Adobe Campaign 설명서의 관련 섹션에 나와 있습니다.

또한 **[!UICONTROL Regional settings]** 드롭다운 목록에서 날짜와 숫자를 표시할 형식을 선택할 수 있습니다.

## 권한 추가 {#access-rights-options}

사용 **[!UICONTROL Access rights]** 탭하여 연산자에 연결된 그룹 및 명명된 권한을 업데이트합니다.

![](assets/operator_profile_security_options.png)

다음 **[!UICONTROL Edit the access parameters...]** 링크를 통해 다음 옵션에 액세스할 수 있습니다.

* 다음 **[!UICONTROL Disable account]** 옵션을 사용하면 운영자의 계정을 비활성화할 수 있습니다. 이 사용자는 더 이상 Adobe Campaign에 액세스하지 않습니다.

   >[!NOTE]
   >
   >계정이 비활성화된 경우에도 운영자는 Campaign에서 경고 또는 알림을 계속 받을 수 있습니다. Adobe 이 운영자에게 Campaign 알림 전송을 중단하려면 해당 프로필에서 이메일 주소를 제거하는 것이 좋습니다.

* 다음 **[!UICONTROL Forbid access from the rich client]** 옵션을 사용하면 Adobe Campaign 사용을 다음으로 제한할 수 있습니다. [웹 액세스](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 또는 API를 통해: Adobe Campaign 클라이언트 콘솔에 더 이상 액세스할 수 없습니다.
* 작업자에게 안전구역을 연결시켜 줄 수 있습니다. 자세한 정보는 이 [페이지](../../installation/using/security-zones.md)를 참조하십시오.
* 적절한 링크를 사용하여 신뢰할 수 있는 IP 마스크를 정의할 수도 있습니다.

   운영자는 IP 주소가 이 목록에 있는 경우 암호를 입력하지 않고 Adobe Campaign에 연결할 수 있습니다.

   다음 예제와 같이 암호 없이 연결하도록 승인될 IP 주소 집합을 지정할 수도 있습니다.

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >플랫폼에 대한 액세스를 안전하게 유지하려면 이 옵션을 신중하게 사용해야 합니다.

* 다음 **[!UICONTROL Restrict to information found in sub-folders of:]** 옵션을 사용하면 폴더 운영자에게 귀속되는 권한을 제한할 수 있습니다. 이 옵션에 지정된 노드의 하위 폴더만 사용자에게 표시됩니다.

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >이는 매우 엄격한 제한이며, 신중하게 사용해야 합니다. 이 유형의 권한으로 로그인한 운영자는 지정된 폴더의 콘텐츠만 볼 수 있으며 탐색기를 통해 트리의 다른 노드에 액세스할 수 없습니다. 그러나 이 운영자가 액세스할 수 있는 기능(예: 워크플로우)에 따라 사용자는 일반적으로 액세스할 수 없는 노드에 저장된 데이터를 표시할 수 있습니다.

### 설정 확인 {#check-settings}

다음 **[!UICONTROL Audit]** 탭에서는 연산자와 관련된 정보를 볼 수 있습니다. 조작자의 개입 영역에 정의된 설정을 기반으로 다양한 탭이 자동으로 추가됩니다.

다음에 액세스할 수 있습니다.

* 연산자에 연결된 폴더의 권한 목록입니다.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >자세한 내용은 다음을 참조하십시오. [폴더 액세스 관리](#folder-access-management).

* 연산자 승인 로그.

   ![](assets/operator_profile_validations.png)

* 구독할 토론 포럼 목록입니다.
* 캘린더에 있는 이벤트.
* 할당된 작업 목록입니다.

## 기본 연산자 {#default-operators}

Adobe Campaign은 관리자(&#39;admin&#39;), 청구(&#39;billing&#39;), 모니터링, 웹 애플리케이션 에이전트(&#39;webapp&#39;) 등의 프로필이 기본적으로 구성된 기술 연산자를 사용합니다. 이들 중 일부는 플랫폼에 설치된 애플리케이션 및 옵션에 따라 다릅니다. 예를 들어 &#39;central&#39; 및 &#39;local&#39; 연산자는 Distributed Marketing 옵션이 설치된 경우에만 표시됩니다.

>[!IMPORTANT]
>
>이들 기술 사업자는 플랫폼이 정보 메시지를 반환하면 기본적으로 알림을 받는다. 해당 사용자에게 연락처 이메일을 제공하는 것이 좋습니다.
>
>웹 애플리케이션이 올바르게 작동하도록 하려면 &#39;webapp&#39; 연산자에 대한 특정 지역 설정을 정의하지 않는 것이 좋습니다.

기본적으로 &#39;웹 앱&#39; 기술 운영자는 명명된 관리 권한을 가지므로 보안 위험을 초래할 수 있습니다. 이 문제를 해결하려면 이 권한을 제거하는 것이 좋습니다. 방법은 다음과 같습니다.

1. 다음에서 **[!UICONTROL Administration > Access management > Named rights]** 노드, 클릭 **[!UICONTROL New]** 을 클릭하여 권한을 만들고 이름을 WEBAPP로 지정합니다.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   명명된 권한은 다음에 자세히 설명되어 있습니다. [명명된 권한](#named-rights) 섹션.

1. 다음에서 **[!UICONTROL Administration > Access management > Operators]** 노드에서 웹 응용 프로그램 에이전트 연산자(&#39;webapp&#39;)를 선택합니다.

   다음 항목 선택 **[!UICONTROL Edit]** 탭을 클릭한 다음 **[!UICONTROL Access rights]** 를 탭하고 목록에서 right라는 ADMINISTRATION을 삭제합니다.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   클릭 **[!UICONTROL Add]** 방금 만든 WEBAPP 권한을 선택한 다음 변경 사항을 저장합니다.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. 주로 &#39;수신자&#39; 폴더인 이 연산자와 관련된 폴더에 대한 데이터 읽기 및 쓰기 액세스 권한을 &#39;webapp&#39; 연산자에게 할당합니다.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   트리 폴더에 대한 권한 수정에 대해서는 [폴더 액세스 관리](#folder-access-management) 섹션.

>[!NOTE]
>
>보안 지침에 대한 자세한 내용은 [Adobe Campaign 보안 구성 검사 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html).
