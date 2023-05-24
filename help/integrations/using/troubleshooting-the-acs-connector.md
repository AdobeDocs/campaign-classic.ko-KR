---
product: campaign
title: ACS 커넥터 문제 해결
description: ACS 커넥터 문제 해결
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: integrations
content-type: reference
topic-tags: acs-connector
hide: true
hidefromtoc: true
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 1%

---

# ACS 커넥터 문제 해결{#troubleshooting-the-acs-connector}



구현에 따라 몇 가지 일반적인 문제에 직면할 수 있습니다.

* **Campaign Standard과 Campaign v7 간의 UI 차이점은 무엇입니까?**

   Campaign Standard과 Campaign v7은 매우 유사한 방식으로 작동합니다. 대부분의 개념들은 같지만 경우에 따라 접근법이 조금씩 다를 수 있다. 다음은 ACS 커넥터의 컨텍스트에서 다를 수 있는 몇 가지 개념입니다.

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 수신자 (또는 기타 프로필 차원)<br /> </td> 
   <td> 프로필<br /> </td> 
  </tr> 
  <tr> 
   <td> 목록<br /> </td> 
   <td> 대상자<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 워크플로우, 타겟팅 워크플로우<br /> </td> 
   <td> 워크플로<br /> </td> 
  </tr> 
  <tr> 
   <td> 작업<br /> </td> 
   <td> 캠페인<br /> </td> 
  </tr> 
  <tr> 
   <td> 웹 애플리케이션<br /> </td> 
   <td> 랜딩 페이지<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 지정 테이블 및 스키마 확장<br /> </td> 
   <td> 사용자 지정 리소스 및 리소스 확장<br /> </td> 
  </tr> 
  <tr> 
   <td> 초기 멤버<br /> </td> 
   <td> 테스트 프로필<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **내 Campaign v7 인스턴스의 수신자가 Campaign Standard에 동기화되거나 표시되지 않습니다.**

   이 경우는 다음과 같은 다양한 이유로 발생할 수 있습니다.

   * Campaign v7에서 방금 수신자를 만들거나 업데이트했습니다. 15분마다 동기화가 트리거됩니다. 즉, 업데이트되거나 새로 생성된 수신자는 다음 동기화 후 Campaign Standard에 표시됩니다.
   * 특정 폴더의 수신자만 동기화하도록 구현을 설정할 수 있습니다. 다른 폴더의 수신자는 동기화되지 않습니다.
   * 수신자는 동기화할 수 있지만 Campaign Standard에 표시되지 않습니다. 폴더 권한 매핑을 확인합니다.

* **Campaign Standard에서 쿼리의 기반이 되는 데 필요한 프로필 필드를 찾을 수 없습니다.**

   기본적으로 nms:recipient 테이블의 20개 필드는 Campaign Standard과 동기화됩니다. 동기화된 필드의 세부 목록을 참조하십시오. Campaign Standard에서 검색해야 하는 추가 필드는 컨설턴트가 매핑하고 구성해야 합니다.

   사용하려는 필드를 사용할 수 있는지 확인하려면에서 프로필 리소스 정의를 확인할 수 있습니다 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   또한 수신자에게 첨부되고 nms:recipients와 관련된 테이블에 저장된 모든 데이터는 기본적으로 Campaign Standard에 동기화되지 않습니다.

   관련 데이터를 계속 사용하려면 Campaign v7에서 타깃팅을 수행하고 다음에 설명된 대로 데이터를 추가할 수 있습니다. [대상자 동기화](../../integrations/using/synchronizing-audiences.md) 섹션을 참조하거나 컨설턴트에게 사용자 지정 가능성에 대해 문의할 수 있습니다.

* **Campaign v7에서 기본 nms:recipient가 아닌 다른 프로필 차원을 사용 중인데, 이러한 차원을 Campaign Standard과 동기화하려면 어떻게 해야 합니까?**

   Campaign Standard은 이라는 이름의 고유한 타겟팅 리소스를 사용합니다. **프로필**. Campaign Standard 연결 기능의 기본 구현은 Campaign v7 수신자와 Campaign Standard 프로필 간의 기본 매핑을 제공합니다.

   Campaign v7에서 다른 프로필 차원을 사용하는 경우 또는 여러 프로필 차원을 사용하는 경우 모두 Campaign Standard 프로필로 매핑해야 합니다. 이러한 특정 요구 사항을 해결하려면 컨설턴트에게 문의하십시오.

* **워크플로우를 통해 Campaign Standard과 프로필 목록을 공유하려고 하는데 Campaign Standard에서 대상을 찾을 수 없습니다**.

   대상자는 다음에서 찾을 수 있습니다 **[!UICONTROL Audiences]** Campaign Standard의 메뉴 아래에 있는 메뉴 중에서 하나를 선택합니다. 레이블은 **[!UICONTROL List update]** Campaign v7 워크플로의 활동. 이는 구현 중에 정의된 폴더 매핑의 적용을 받습니다.

   가장 먼저 확인해야 할 사항은 워크플로우가 오류 없이 완료되었는지 여부입니다. 에 오류가 표시되는 경우 **[!UICONTROL List update]** 활동으로, Campaign Standard과의 동기화가 실패할 수 있음을 의미합니다. 무엇이 잘못되었는지 자세히 확인하려면 다음 위치로 이동하십시오. **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. 이 폴더에는 **[!UICONTROL List update]** 활동 실행.

   또한 **[!UICONTROL Share with ACS]** 옵션이에서 선택됨 **[!UICONTROL List update]** 활동 및 워크플로우가 올바르게 실행되었는지 확인합니다.

   목록에 포함된 수신자 프로필은 워크플로우 실행 전에 Campaign Standard과 동기화되어야 합니다. Campaign Standard과 공유되면 목록의 수신자는 Campaign Standard 프로필로 조정되므로 해당 프로필에 존재해야 합니다. Campaign Standard의 프로필로 조정할 수 없는 목록의 수신자는 무시됩니다.

   프로필로 구성된 목록을 공유하고 프로필과 동기화되지 않는 경우 사용할 수 없는 빈 Campaign Standard 대상이 Campaign Standard에 생성됩니다.

* **동기화 워크플로우가 오류 상태에 있다는 알림을 받았습니다. 어떻게 해야 합니까?**

   연결을 테스트하여 Campaign Standard 및 Campaign v7 모두에서 외부 계정 구성을 확인합니다.

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard.
   * **[!UICONTROL acsDefaultAccount]** Campaign v7에서.

* **Campaign v7과 Campaign Standard 간에 폴더를 매핑할 때 사용할 수 있는 보안 그룹이 없습니다.**

   먼저 다음 위치에서 보안 그룹을 동기화해야 합니다 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. 이 작업은 Campaign Standard에서 사용 가능한 보안 그룹을 확인합니다. 동기화된 후에는 폴더 매핑을 구성할 때 보안 그룹을 찾을 수 있습니다.

* **Campaign Standard에서 프로필, 대상자 또는 랜딩 페이지를 편집할 수 없습니다. 어떤 의미입니까?**

   Campaign v7에서 동기화된 리소스는 데이터 일관성을 보장하기 위해 Campaign Standard에서 읽기 전용 모드에 있습니다. 이러한 요소 중 하나를 편집해야 하는 경우 Campaign v7에서 편집한 다음 Campaign Standard 변경 사항을 복제할 수 있습니다.

* **에서 오류 발생 [ACS] 프로필 게재 로그 복제 워크플로우입니다. 어떻게 해야 합니까?**

   Campaign Classic 인스턴스와 Campaign Standard 인스턴스가 모두 추적된 URL이 있는 이메일을 보내는 데 사용되는 경우 동기화 중에 중복 URL tagIds 문제가 발생할 수 있습니다. 이 경우 **[ACS] 프로필 게재 로그 복제** (newRcpDeliveryLogReplication) 워크플로우가 실패하고 다음 오류가 발생합니다.

   ```PGS-220000 PostgreSQL error: ERROR: duplicate key value violates unique constraint "nmstrackingurl_tagid" DETAIL: Key (stagid) = (1c7bdec2) already exists.```

   문제를 해결하고 다시 발생하지 않도록 하려면 **추적 URL 업데이트** (writerTrackingUrls) 활동을 워크플로우에서 실행하고 &quot;ACS&quot; 접두사를 @tagId 소스 표현식에 추가합니다.
