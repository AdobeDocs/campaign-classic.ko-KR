---
solution: Campaign Classic
product: campaign
title: 개인 정보 보호 규정 워크플로우
description: 개인 정보 보호 규정 워크플로우에 대한 자세한 내용
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 10%

---


# 개인 정보 보호 규정{#general-data-protection-regulation-gdpr}

아래에 자세히 설명된 워크플로우는 기본적으로 **개인 정보 보호 규정** 모듈과 함께 설치됩니다. For more on this module, refer to this [article](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">개인 정보 요청 수집</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> 이 워크플로우는 Adobe Campaign에 저장된 수신자 데이터를 생성하여 개인 정보 요청의 화면에서 다운로드할 수 있도록 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">개인 정보 요청 데이터 삭제</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 이 워크플로우는 Adobe Campaign에 저장된 받는 사람의 데이터를 삭제합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">개인 정보 요청 정리</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 이 워크플로우는 90일 이전의 액세스 요청 파일을 지웁니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

