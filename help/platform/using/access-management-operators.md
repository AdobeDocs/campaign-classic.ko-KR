---
solution: Campaign Classic
product: campaign
title: 캠페인 연산자 시작하기
description: 캠페인 사용자를 만들고 관리하는 방법에 대해 알아봅니다.
feature: Access Management
role: Business Practitioner, Administrator
level: Beginner
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 2%

---


# 연산자 만들기 및 관리 {#operators}

## 캠페인 연산자 {#about-operators} 시작하기

연산자는 로그인하고 작업을 수행할 권한이 있는 Adobe Campaign 사용자입니다.

기본적으로 연산자는 **[!UICONTROL Administration > Access management > Operators]** 노드에 저장됩니다.

![](assets/s_ncs_user_list_operators.png)

연산자를 수동으로 만들거나 기존 LDAP 디렉토리에 매핑할 수 있습니다.

연산자를 만드는 전체 절차는 [이 페이지](#creating-an-operator)에 설명되어 있습니다.

Adobe Campaign 및 LDAP 통합에 대한 자세한 내용은 [이 페이지](../../installation/using/connecting-through-ldap.md)를 참조하십시오.

>[!IMPORTANT]
>
>연산자는 인스턴스에 로그온하려면 보안 영역에 연결해야 합니다. Adobe Campaign의 보안 영역에 대한 자세한 내용은 [이 페이지](../../installation/using/security-zones.md)를 참조하십시오.

사용자는 Adobe ID을 사용하여 Adobe Campaign에 직접 연결할 수도 있습니다. 자세한 정보는 이 [페이지](../../integrations/using/about-adobe-id.md)를 참조하십시오.

## 연산자 {#creating-an-operator} 만들기

새 연산자를 만들고 권한을 부여하려면 아래 단계를 따르십시오.

1. 연산자 목록 위에 있는 **[!UICONTROL New]** 단추를 클릭하고 새 연산자의 세부 정보를 입력합니다.

   ![](assets/s_ncs_user_operator_new.png)

1. 사용자의 **[!UICONTROL Identification parameters]**&#x200B;을(를) 지정합니다.로그인, 암호 및 이름입니다. 연산자가 로그인과 암호를 사용하여 Adobe Campaign에 로그온합니다. 사용자가 로그온하면 **[!UICONTROL Tools > Change password]** 메뉴를 통해 암호를 변경할 수 있습니다. 연산자의 이메일은 연산자가 승인을 처리할 때 알림을 수신할 수 있도록 해주므로 매우 중요합니다.

   이 섹션에서는 연산자를 조직 엔티티에 연결할 수도 있습니다. 자세한 내용은 [이 페이지](../../campaign/using/about-distributed-marketing.md)를 참조하십시오.

1. **[!UICONTROL Operator access rights]** 섹션에서 연산자에 부여된 권한을 선택합니다.

   연산자에 권한을 할당하려면 권한 목록 위에 있는 **[!UICONTROL Add]** 단추를 클릭한 다음 사용 가능한 그룹 목록에서 연산자 그룹을 선택합니다.

   ![](assets/s_ncs_user_permissions_operators.png)

   하나 이상의 명명된 권한을 선택할 수도 있습니다([명명된 권한](#named-rights) 참조). 이렇게 하려면 **[!UICONTROL Folder]** 필드 오른쪽에 있는 화살표를 클릭하고 **[!UICONTROL Named rights]**:

   ![](assets/s_ncs_user_rights_operators.png)

   할당할 그룹 및/또는 명명된 권한을 선택하고 **[!UICONTROL OK]** 을 클릭하여 유효성을 확인합니다.

1. **[!UICONTROL Ok]**&#x200B;을 클릭하여 연산자를 만듭니다.기존 연산자 목록에 프로필이 추가됩니다.

   ![](assets/operator_profile_new.png)

>[!NOTE]
>
>새 연산자 폴더를 만들어 필요에 따라 연산자를 구성할 수 있습니다. 이렇게 하려면 연산자 폴더를 마우스 오른쪽 단추로 클릭하고 **[!UICONTROL Add an 'Operators' folder]**&#x200B;을 선택합니다.

연산자 프로필이 만들어지면 해당 정보를 추가하거나 업데이트할 수 있습니다. 이렇게 하려면 **[!UICONTROL Edit]** 탭을 클릭합니다.

![](assets/operator_edit_profile.png)

>[!NOTE]
>
>**[!UICONTROL Session timeout]** 필드에서 FDA 세션 시간 초과 전의 지연을 조정할 수 있습니다. 자세한 내용은 [통합 데이터 액세스 정보](../../installation/using/about-fda.md)를 참조하십시오.

## 연산자의 표준 시간대 {#time-zone-of-the-operator} 정의

**[!UICONTROL General]** 탭에서 연산자의 시간대를 선택할 수 있습니다. 기본적으로 연산자는 서버 시간대에서 작동합니다. 하지만 드롭다운 목록을 사용하여 다른 시간대를 선택할 수 있습니다.

시간대 구성은 [이 페이지](../../installation/using/time-zone-management.md)에 설명되어 있습니다.

>[!NOTE]
>
>다양한 시간대 내의 공동 작업은 UTC에 날짜 저장을 필요로 합니다. 날짜는 다음 컨텍스트의 해당 시간대에서 변환됩니다.날짜가 사용자 표준 시간대로 표시될 때, 파일을 가져오고 내보낼 때, 이메일 배달을 예약할 때, 작업이 워크플로우에서 예약된 시간(스케줄러, 대기, 시간 제한 등)
>
>이러한 컨텍스트에 연결된 제약 조건 및 권장 사항은 Adobe Campaign 문서의 관련 섹션에 표시됩니다.

또한 **[!UICONTROL Regional settings]** 드롭다운 목록을 사용하여 날짜 및 숫자를 표시할 형식을 선택할 수 있습니다.

## 권한 추가 {#access-rights-options}

**[!UICONTROL Access rights]** 탭을 사용하여 연산자에 연결된 그룹과 명명된 권한을 업데이트합니다.

![](assets/operator_profile_security_options.png)

**[!UICONTROL Edit the access parameters...]** 링크를 사용하면 다음 옵션에 액세스할 수 있습니다.

* **[!UICONTROL Disable account]** 옵션을 사용하여 연산자의 계정을 비활성화할 수 있습니다.더 이상 Adobe Campaign에 액세스할 수 없습니다.

   >[!NOTE]
   >
   >계정이 비활성화되어도 운영자는 여전히 Campaign에서 알림 또는 알림을 받을 수 있습니다. 이 연산자에 대한 캠페인 알림 전송을 중지하려면 Adobe은 자신의 프로필에서 이메일 주소를 제거하는 것이 좋습니다.

* **[!UICONTROL Forbid access from the rich client]** 옵션을 사용하면 Adobe Campaign의 사용을 [웹 액세스](../../platform/using/adobe-campaign-workspace.md#console-and-web-access) 또는 API를 통해 제한할 수 있습니다.더 이상 Adobe Campaign 클라이언트 콘솔에 액세스할 수 없습니다.
* 안전구역을 운영자와 연결시킬 수 있습니다 자세한 정보는 이 [페이지](../../installation/using/security-zones.md)를 참조하십시오.
* 적절한 링크를 사용하여 신뢰할 수 있는 IP 마스크를 정의할 수도 있습니다.

   IP 주소가 이 목록에 있는 경우 연산자를 사용하면 암호를 입력하지 않고도 Adobe Campaign에 연결할 수 있습니다.

   다음 예제와 같이 암호 없이 연결할 수 있도록 인증할 IP 주소 세트를 지정할 수도 있습니다.

   ![](assets/operator_trustip.png)

   >[!NOTE]
   >
   >플랫폼에 안전하게 액세스하려면 이 옵션을 신중히 사용해야 합니다.

* **[!UICONTROL Restrict to information found in sub-folders of:]** 옵션을 사용하면 폴더 연산자에 속하는 권한을 제한할 수 있습니다. 이 옵션에 지정된 노드의 하위 폴더만 사용자에게 표시됩니다.

   ![](assets/s_ncs_user_restrictions_operators.png)

   >[!IMPORTANT]
   >
   >이것은 매우 엄격한 제한 사항이므로 주의해서 사용해야 한다. 이 유형의 권한으로 로그인한 연산자는 지정된 폴더의 컨텐츠만 볼 수 있고 탐색기를 통해 트리의 다른 노드에 액세스할 수 없습니다. 그러나 액세스할 수 있는 기능에 따라 달라집니다(예:워크플로우)에서 볼 수 없는 노드에 일반적으로 저장되는 데이터를 표시할 수 있습니다.

### 설정 확인 {#check-settings}

**[!UICONTROL Audit]** 탭에서는 연산자와 관련된 정보를 볼 수 있습니다. 연산자의 개입 영역에 정의된 설정을 기반으로 다양한 탭이 자동으로 추가됩니다.

다음 항목에 액세스할 수 있습니다.

* 연산자에 연결된 폴더의 권한 목록.

   ![](assets/operator_folder_permissions.png)

   >[!NOTE]
   >
   >자세한 내용은 [폴더 액세스 관리](#folder-access-management)를 참조하십시오.

* 운영자 승인 로그.

   ![](assets/operator_profile_validations.png)

* 가입한 토론 포럼 목록.
* 달력 내 이벤트.
* 할당된 작업 목록입니다.

## 기본 연산자 {#default-operators}

Adobe Campaign은 기본적으로 프로파일을 구성하는 기술 운영업체를 사용합니다.관리자(&#39;관리자&#39;), 과금(&#39;과금&#39;), 모니터링, 웹 애플리케이션 에이전트(&#39;웹 앱&#39;) 등 이러한 옵션 중 일부는 플랫폼에 설치된 애플리케이션과 옵션에 따라 다릅니다.예를 들어 분산 마케팅 옵션이 설치된 경우에만 &#39;central&#39; 및 &#39;local&#39; 연산자를 볼 수 있습니다.

>[!IMPORTANT]
>
>정보 메시지가 플랫폼에서 반환되면 이러한 기술 운영자에게 기본적으로 통보됩니다. 해당 고객에게 연락처 이메일을 제공하는 것이 좋습니다.
>
>웹 응용 프로그램이 제대로 작동하는지 확인하려면 &#39;webapp&#39; 연산자에 대한 특정 지역 설정을 정의하지 않는 것이 좋습니다.

기본적으로 &#39;webapp&#39; 기술 운영자에게는 지정된 ADMINISTRATION 권한이 있으며 이로 인해 보안 위험이 발생할 수 있습니다. 이 문제를 해결하려면 이 권한을 제거하는 것이 좋습니다. 방법은 다음과 같습니다.

1. **[!UICONTROL Administration > Access management > Named rights]** 노드에서 **[!UICONTROL New]**&#x200B;을 클릭하여 권한을 만들고 이름을 WEBAPP로 지정합니다.

   ![](assets/s_ncs_default_operators_webapp_right.png)

   명명된 권한은 [명명된 권한](#named-rights) 섹션에 자세히 설명되어 있습니다.

1. **[!UICONTROL Administration > Access management > Operators]** 노드에서 웹 응용 프로그램 에이전트 연산자(&#39;webapp&#39;)를 선택합니다.

   **[!UICONTROL Edit]** 탭을 선택한 다음 **[!UICONTROL Access rights]** 탭을 선택하고 목록에서 바로 명명된 ADMINISTRATION을 삭제합니다.

   ![](assets/s_ncs_default_operators_webapp_admin_right.png)

   **[!UICONTROL Add]**&#x200B;을(를) 클릭하고 방금 만든 WEBAPP을 선택한 다음 변경 내용을 저장합니다.

   ![](assets/s_ncs_default_operators_webapp_webapp_right.png)

1. &#39;webapp&#39; 연산자가 주로 &#39;받는 사람&#39; 폴더인 이 연산자와 관련된 폴더에 데이터 액세스 권한을 읽고 쓰십시오.

   ![](assets/s_ncs_default_operators_webapp_folder_access.png)

   트리 폴더의 권한 수정은 [폴더 액세스 관리](#folder-access-management) 섹션에 자세히 설명되어 있습니다.

>[!NOTE]
>
>보안 지침에 대한 자세한 내용은 [Adobe Campaign 보안 구성 검사 목록](https://helpx.adobe.com/kr/campaign/kb/acc-security.html)을 참조하십시오.
