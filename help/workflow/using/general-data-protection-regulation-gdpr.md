---
product: campaign
title: 개인 정보 보호 규정 워크플로
description: 개인 정보 보호 규정 워크플로우에 대해 자세히 알아보십시오
hide: true
feature: Workflows, Privacy
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 7%
---

# 개인 정보 보호 규정{#general-data-protection-regulation-gdpr}



아래에 설명된 워크플로는 기본적으로 **개인 정보 보호 규정** 모듈과 함께 설치됩니다. 이 모듈에 대한 자세한 내용은 이 [문서](https://helpx.adobe.com/kr/campaign/kb/acc-privacy.html)를 참조하세요.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>레이블</strong><br /> </td> 
   <td> <strong>내부 이름</strong><br /> </td> 
   <td> <strong>설명</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">개인 정보 보호 요청 수집</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> 이 워크플로우는 Adobe Campaign에 저장된 수신자의 데이터를 생성하여 개인 정보 보호 요청의 화면에서 다운로드할 수 있도록 합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">개인 정보 보호 요청 데이터 삭제</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 이 워크플로는 Adobe Campaign에 저장된 받는 사람의 데이터를 삭제합니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">개인 정보 보호 요청 정리</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 이 워크플로에서는 90일 이전의 액세스 요청 파일을 삭제합니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

