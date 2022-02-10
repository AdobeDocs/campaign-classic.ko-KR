---
product: campaign
title: ACS 커넥터 문제 해결
description: ACS 커넥터 문제 해결
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 4693dca1-ee55-43f0-b3dc-62a5b67a8058
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# ACS 커넥터 문제 해결{#troubleshooting-the-acs-connector}

![](../../assets/v7-only.svg)

구현에 따라 몇 가지 일반적인 문제가 발생할 수 있습니다.

* **Campaign Standard과 Campaign v7 간의 UI 차이점은 무엇입니까?**

   Campaign Standard 및 Campaign v7은 매우 유사한 방식으로 작동합니다. 대부분의 개념은 동일하지만, 경우에 따라 접근 방식이 약간 다를 수 있습니다. 다음은 ACS 커넥터 컨텍스트에서 다를 수 있는 몇 가지 개념입니다.

<table> 
 <thead> 
  <tr> 
   <th> Campaign v7<br /> </th> 
   <th> Campaign Standard<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 수신자(또는 기타 프로필 차원)<br /> </td> 
   <td> 프로필<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> 대상자<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 워크플로우, 타겟팅 워크플로우<br /> </td> 
   <td> 워크플로우<br /> </td> 
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

* **Campaign v7 인스턴스의 수신자가 동기화되거나 Campaign Standard에 표시되지 않습니다.**

   이 사례는 다음과 같은 여러 이유로 발생할 수 있습니다.

   * 수신자는 Campaign v7에서 방금 생성되었거나 업데이트되었습니다. 동기화는 15분마다 트리거됩니다. 즉, 업데이트되거나 새로 생성된 수신자는 다음 동기화 후 Campaign Standard에 표시됩니다.
   * 특정 폴더의 수신자만 동기화하도록 구현을 설정할 수 있습니다. 다른 폴더의 수신자가 동기화되지 않습니다.
   * 수신자는 동기화할 수 있지만 Campaign Standard에 표시되지 않습니다. 폴더 권한 매핑을 확인합니다.

* **Campaign Standard에서 쿼리를 기반으로 하는 프로필 필드를 찾을 수 없습니다.**

   기본적으로 nms:recipient 테이블의 필드 20개가 Campaign Standard과 동기화됩니다. 동기화된 필드의 세부 목록을 참조하십시오. Campaign Standard에서 검색해야 하는 추가 필드는 컨설턴트가 매핑하고 구성해야 합니다.

   사용할 필드를 사용할 수 있도록 하기 위해 다음 위치에서 프로필 리소스 정의를 확인할 수 있습니다 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   또한 수신자에 첨부되고 nms:recipients와 관련된 테이블에 저장된 모든 데이터는 기본적으로 Campaign Standard과 동기화되지 않습니다.

   관련 데이터를 계속 사용하려면, Campaign v7에서 타깃팅을 수행하고 다음에서 설명한 대로 추가 데이터를 추가할 수 있습니다. [대상자 동기화](../../integrations/using/synchronizing-audiences.md) 섹션을 참조하거나 컨설턴트에게 문의하여 사용자 지정 가능성을 탐색할 수 있습니다.

* **Campaign v7에서 기본 nms:recipient가 아닌 다른 프로필 차원을 사용하고 있습니다. Campaign Standard과 동기화하려면 어떻게 해야 합니까?**

   Campaign Standard은 이름이 인 고유한 타겟팅 리소스를 사용합니다 **프로필**. Campaign Standard 연결 기능의 기본 구현에서는 Campaign v7 수신자와 Campaign Standard 프로필 간에 기본 매핑을 제공합니다.

   Campaign v7에서 다른 프로필 차원을 사용하거나 여러 차원을 사용하는 경우 모두 Campaign Standard 프로필으로 매핑되어야 합니다. 이러한 특정 요구 사항을 해결하려면 컨설턴트를 참조하십시오.

* **워크플로우를 통해 Campaign Standard과 프로필 목록을 공유하고 싶지만 Campaign Standard에서 대상자를 찾을 수 없습니다**.

   대상은 **[!UICONTROL Audiences]** 메뉴의 Campaign Standard. 여기에 지정된 레이블이 있습니다. **[!UICONTROL List update]** 활동 을 만들 수 있습니다. 이들은 구현 중에 정의된 폴더 매핑을 따릅니다.

   첫 번째 확인할 사항은 워크플로우가 오류 없이 완료되었는지 여부입니다. 에 오류가 있는 것을 발견하면 **[!UICONTROL List update]** 활동: Campaign Standard과 동기화가 실패했음을 의미합니다. 잘못된 사항에 대한 자세한 내용을 보려면 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. 이 폴더에는 **[!UICONTROL List update]** 활동 실행을 참조하십시오.

   또한 **[!UICONTROL Share with ACS]** 옵션이 선택되어 있습니다. **[!UICONTROL List update]** 활동 및 워크플로우가 올바르게 실행되었는지 확인합니다.

   목록에 포함된 수신자 프로필은 워크플로우 실행 전에 Campaign Standard과 동기화되어야 합니다. Campaign Standard과 공유되면 목록의 수신자는 Campaign Standard 프로필과 조정됩니다. 즉, 해당 프로필에는 존재해야 합니다. Campaign Standard의 프로필과 조정할 수 없는 목록의 수신자는 무시됩니다.

   프로필로 구성된 목록을 공유하고 Campaign Standard과 동기화된 항목이 없는 경우, 사용할 수 없는 Campaign Standard에 빈 쿼리 대상이 만들어집니다.

* **동기화 워크플로우가 오류 상태라는 알림을 받았습니다. 어떻게 해야 합니까?**

   연결을 테스트하여 Campaign Standard 및 Campaign v7에서 모두 외부 계정 구성을 확인합니다.

   * **[!UICONTROL acsDefaultRelayAccount]** Campaign Standard에서 확인하십시오.
   * **[!UICONTROL acsDefaultAccount]** Campaign v7에서 사용할 수 있습니다.

* **Campaign v7와 Campaign Standard 간에 폴더를 매핑할 때 사용할 수 있는 보안 그룹이 없습니다.**

   먼저 보안 그룹을 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. 이 작업은 Campaign Standard에서 사용할 수 있는 보안 그룹을 확인합니다. 동기화된 후에는 폴더 매핑을 구성할 때 보안 그룹을 찾을 수 있습니다.

* **Campaign Standard에서 프로필, 대상자 또는 랜딩 페이지를 편집할 수 없습니다. 어떤 의미입니까?**

   Campaign v7에서 동기화된 리소스는 데이터 일관성을 위해 Campaign Standard에서 읽기 전용 모드에 있습니다. 이러한 요소 중 하나를 편집해야 하는 경우 Campaign v7에서 편집한 다음 Campaign Standard에서 변경 사항을 복제할 수 있습니다.
