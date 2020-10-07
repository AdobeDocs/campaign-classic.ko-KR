---
title: ACS 커넥터 문제 해결
seo-title: ACS 커넥터 문제 해결
description: ACS 커넥터 문제 해결
seo-description: null
page-status-flag: never-activated
uuid: aef85b74-0388-44f8-b864-21db136a692c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: acs-connector
discoiquuid: 538d3b48-ff39-463f-878d-ebe085057129
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 0%

---


# Troubleshooting the ACS Connector{#troubleshooting-the-acs-connector}

구현에 따라 몇 가지 일반적인 문제가 발생할 수 있습니다.

* **Campaign Standard과 Campaign v7의 UI 차이는 무엇입니까?**

   Campaign Standard 및 Campaign v7은 매우 유사한 방식으로 작동합니다. 대부분의 개념은 동일하지만, 어떤 경우에는 접근법이 약간 다를 수 있다. 다음은 ACS 커넥터 컨텍스트와 다를 수 있는 몇 가지 개념입니다.

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
   <td> profiles<br /> </td> 
  </tr> 
  <tr> 
   <td> list<br /> </td> 
   <td> audience<br /> </td> 
  </tr> 
  <tr> 
   <td> 캠페인 워크플로우, 타깃팅 워크플로우<br /> </td> 
   <td> workflows<br /> </td> 
  </tr> 
  <tr> 
   <td> 운영<br /> </td> 
   <td> campaigns<br /> </td> 
  </tr> 
  <tr> 
   <td> web applications<br /> </td> 
   <td> landing pages<br /> </td> 
  </tr> 
  <tr> 
   <td> 사용자 정의 테이블 및 스키마 확장<br /> </td> 
   <td> 사용자 지정 리소스 및 리소스 확장<br /> </td> 
  </tr> 
  <tr> 
   <td> 시드 멤버<br /> </td> 
   <td> test profiles<br /> </td> 
  </tr> 
 </tbody> 
</table>

* **내 Campaign v7 인스턴스의 수신자가 동기화되거나 Campaign Standard에 표시되지 않습니다.**

   이 사례는 다음과 같은 여러 이유로 발생할 수 있습니다.

   * 수신자는 Campaign v7에서 방금 생성되었거나 업데이트되었습니다. 동기화는 15분마다 트리거됩니다. 즉, 업데이트되거나 새로 만든 받는 사람이 다음 동기화 후 Campaign Standard에 표시됩니다.
   * 특정 폴더의 수신자만 동기화하도록 구현을 설정할 수 있습니다. 다른 폴더의 받는 사람이 동기화되지 않습니다.
   * 수신자는 동기화될 수 있지만 Campaign Standard에 표시되지 않습니다. 폴더 권한 매핑을 확인합니다.

* **Campaign Standard에서 쿼리를 기반으로 하는 프로필 필드를 찾을 수 없습니다.**

   기본적으로 nms:recipient 테이블의 20개 필드가 Campaign Standard과 동기화됩니다. 동기화된 필드의 세부 목록을 참조하십시오. Campaign Standard에서 검색해야 하는 추가 필드는 컨설턴트가 매핑하고 구성해야 합니다.

   사용할 필드를 사용할 수 있는지 확인하려면 프로필 리소스 정의를 확인할 수 있습니다 **[!UICONTROL Administration > Development > Diagnosis > Data schemas]**.

   또한, 수신자에게 첨부된 데이터 및 nms:receividents와 관련된 테이블에 저장된 모든 데이터는 기본적으로 Campaign Standard으로 동기화되지 않습니다.

   관련 데이터를 계속 사용하려면 Campaign v7에서 타깃팅을 수행하고 대상 [](../../integrations/using/synchronizing-audiences.md) 동기화 섹션에 설명된 대로 추가 데이터를 추가하거나 컨설턴트를 참조하여 사용자 정의 가능성을 탐색할 수 있습니다.

* **Campaign v7에서 기본 nms:recipient보다 다른 프로필 차원을 사용하고 있습니다. 이러한 차원을 Campaign Standard과 동기화하려면 어떻게 해야 합니까?**

   Campaign Standard은 프로필 이름을 지정하는 고유한 타깃팅 리소스를 **사용합니다**. Campaign Standard 연결 기능의 기본 구현은 Campaign v7 받는 사람과 Campaign Standard 프로필 간의 기본 매핑을 제공합니다.

   Campaign v7에서 다른 프로필 차원을 사용하거나 여러 개의 프로필 차원을 사용하는 경우 모두 Campaign Standard 프로필과 매핑되어야 합니다. 이러한 특정 요구 사항을 해결하려면 컨설턴트를 참조하십시오.

* **워크플로우를 통해 Campaign Standard과 프로필 목록을 공유하고 싶지만 Campaign Standard에서 고객을 찾을 수 없습니다**.

   대상은 Campaign Standard의 **[!UICONTROL Audiences]** 메뉴에서 찾을 수 있습니다. 캠페인 v7 워크플로의 **[!UICONTROL List update]** 활동에 지정된 레이블이 있습니다. 구현 중에 정의된 폴더 매핑이 적용됩니다.

   첫 번째 확인은 워크플로우가 오류 없이 완료되었는지 여부입니다. 활동에 오류가 있는 경우 Campaign Standard와의 동기화가 실패했을 수 **[!UICONTROL List update]** 있습니다. 잘못된 내용에 대한 자세한 내용을 보려면 **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**&#x200B;를 참조하십시오. 이 폴더에는 활동 실행에 의해 트리거된 동기화 워크플로우가 **[!UICONTROL List update]** 포함됩니다.

   또한, 이 **[!UICONTROL Share with ACS]** 옵션이 **[!UICONTROL List update]** 활동에서 체크 인되어 있고 워크플로우가 올바르게 실행되었는지 확인하십시오.

   목록에 포함된 수신자 프로필은 워크플로우 실행 전에 Campaign Standard과 동기화되어야 합니다. Campaign Standard과 공유하면 목록의 수신자가 Campaign Standard 프로필과 조정됩니다. 즉, 목록에 있어야 합니다. Campaign Standard의 프로필과 상호 작용할 수 없는 목록의 받는 사람은 무시됩니다.

   프로필로 구성된 목록을 공유하고 Campaign Standard과 동기화되지 않은 경우 Campaign Standard에 사용할 수 없는 빈 쿼리 대상을 만듭니다.

* **동기화 워크플로가 오류 상태라는 알림을 받았습니다. 어떻게 해야 합니까?**

   연결을 테스트하여 Campaign Standard 및 Campaign v7의 외부 계정 구성을 확인합니다.

   * **[!UICONTROL acsDefaultRelayAccount]** campaign standard에서
   * **[!UICONTROL acsDefaultAccount]** 캠페인 v7에서

* **Campaign v7과 Campaign Standard 간에 폴더를 매핑할 때 사용할 수 있는 보안 그룹이 없습니다.**

   먼저 보안 그룹을 동기화해야 합니다 **[!UICONTROL Administration > ACS Connector > Rights management > Security groups]**. 이 작업은 Campaign Standard에서 사용할 수 있는 보안 그룹을 확인합니다. 동기화한 후에는 폴더 매핑을 구성할 때 보안 그룹을 찾을 수 있습니다.

* **Campaign Standard에서 프로필, 대상 또는 랜딩 페이지를 편집할 수 없습니다. 무슨 뜻이죠?**

   Campaign v7에서 동기화된 리소스는 Campaign Standard에서 읽기 전용 모드로 되어 데이터 일관성을 보장합니다. 이러한 요소 중 하나를 편집해야 하는 경우 Campaign v7에서 편집한 다음 Campaign Standard에서 변경 사항을 복제할 수 있습니다.

