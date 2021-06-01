---
product: campaign
title: 문제 해결
description: 문제 해결
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---

# 문제 해결{#troubleshooting}

오류가 발생하는 경우 다음 요소가 올바르게 구성되어 있는지 확인하십시오.

* **외부 계정**

   **[!UICONTROL Administration > Platform > External accounts]**&#x200B;에서 다음 외부 SFTP 계정이 올바르게 구성되었는지 확인합니다. 언급된 SFTP 서버는 컨설턴트가 Adobe Experience Cloud에 구성했어야 합니다.

   * **[!UICONTROL importSharedAudience]** :대상을 가져오는 데 사용되는 SFTP 계정입니다.
   * **[!UICONTROL exportSharedAudience]** :대상 내보내기를 위한 SFTP 계정입니다.

* **AMC 데이터 소스**

   **[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;에서 AMC 데이터 소스가 제대로 설정되었는지 확인합니다.

People 핵심 서비스를 통해 대상을 공유하거나 대상을 가져올 때 일부 데이터가 누락될 수 있습니다. 프로필 차원과 조정할 수 있는 ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)의 레코드만 전송됩니다. Adobe Campaign에서 인식하지 못하는 사람 핵심 서비스 세그먼트의 ID는 가져올 수 없습니다.
