---
title: 문제 해결
seo-title: 문제 해결
description: 문제 해결
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 문제 해결{#troubleshooting}

오류가 발생하는 경우 다음 요소가 올바르게 구성되었는지 확인하십시오.

* **외부 계정**

   에서 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;다음 외부 SFTP 계정이 올바르게 구성되어 있는지 확인합니다. 언급된 SFTP 서버는 컨설턴트가 Adobe Experience Cloud에 구성했어야 합니다.

   * **[!UICONTROL importSharedAudience]** :대상 가져오기 전용 SFTP 계정.
   * **[!UICONTROL exportSharedAudience]** :대상 내보내기를 위한 SFTP 계정.

* **AMC 데이터 소스**

   에서 **[!UICONTROL Administration > Platform > AMC Data sources]** AMC 데이터 소스가 제대로 설정되어 있는지 확인합니다.

사람 코어 서비스를 통해 대상을 공유하거나 대상을 가져올 때 일부 데이터가 누락될 수 있습니다. ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)가 프로필 차원과 조정될 수 있었던 레코드만 전송됩니다. Adobe Campaign에서 인식할 수 없는 사람 핵심 서비스 세그먼트의 ID는 가져올 수 없습니다.
