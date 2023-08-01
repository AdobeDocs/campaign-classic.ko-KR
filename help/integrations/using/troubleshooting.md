---
product: campaign
title: 문제 해결
description: 문제 해결
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v7: label="v7" type="Informative" tooltip="Campaign Classic v7에 적용"
badge-v8: label="v8" type="Positive" tooltip="Campaign v8에도 적용됩니다."
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# 문제 해결{#troubleshooting}



오류가 발생한 경우 다음 요소가 올바르게 구성되었는지 확인하십시오.

* **외부 계정**

  위치 **[!UICONTROL Administration > Platform > External accounts]**, 다음 외부 SFTP 계정이 올바르게 구성되었는지 확인하십시오. 언급된 SFTP 서버는 컨설턴트가 Adobe Experience Cloud에서 구성해야 합니다.

   * **[!UICONTROL importSharedAudience]** : 대상자 가져오기 전용 SFTP 계정
   * **[!UICONTROL exportSharedAudience]** : 대상자 내보내기 전용 SFTP 계정

* **AMC 데이터 소스**

  위치 **[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;를 클릭하여 AMC 데이터 소스가 제대로 설정되어 있는지 확인합니다.

People 핵심 서비스를 통해 대상자를 공유하거나 대상자를 가져올 때 일부 데이터가 누락될 수 있습니다. ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)가 프로필 차원과 조정될 수 있는 레코드만 전송됩니다. Adobe Campaign에서 인식하지 못하는 사람 핵심 서비스 세그먼트의 ID는 가져오지 않습니다.
