---
solution: Campaign Classic
product: campaign
title: 문제 해결
description: 문제 해결
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# 문제 해결{#troubleshooting}

오류가 발생한 경우 다음 요소가 올바르게 구성되어 있는지 확인하십시오.

* **외부 계정**

   **[!UICONTROL Administration > Platform > External accounts]**&#x200B;에서 다음 외부 SFTP 계정이 올바르게 구성되어 있는지 확인합니다. 언급된 SFTP 서버는 컨설턴트가 Adobe Experience Cloud에 구성했어야 합니다.

   * **[!UICONTROL importSharedAudience]** :대상을 가져오는 데 사용되는 SFTP 계정입니다.
   * **[!UICONTROL exportSharedAudience]** :대상 내보내기를 전용 SFTP 계정.

* **AMC 데이터 소스**

   **[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;에서 AMC 데이터 소스가 제대로 설정되어 있는지 확인합니다.

사람 핵심 서비스를 통해 대상을 공유하거나 대상을 가져올 때 일부 데이터가 누락될 수 있습니다. ID(&#39;방문자 ID&#39; 또는 &#39;선언된 ID&#39;)를 프로필 차원과 조정할 수 있는 레코드만 전송됩니다. Adobe Campaign에서 인식하지 못하는 사람 핵심 서비스 세그먼트의 ID는 가져오지 않습니다.
