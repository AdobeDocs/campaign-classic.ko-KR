---
product: campaign
title: 기술 정보 - Adobe Campaign - Apache 버전 보안 업데이트
description: Adobe Campaign - Apache 버전 보안 업데이트
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: a3eae4e253f66f5a651ffe0458f60b1f8bdf2258
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Adobe Campaign - Apache 버전 보안 업데이트 {#apache-update}

>[!CAUTION]
>This article applies to: **Campaign Classic v7 Managed Services** customers, **Campaign v8** customers and **Campaign Standard** customers.

Adobe Campaign은 타사 도구와 연동되며, 지원되는 버전만 구현하고 최신 수정 및 개선 사항을 활용할 수 있도록 정기적으로 호환성이 업데이트됩니다.

Adobe Campaign에는 HTTP를 통해 애플리케이션 서버에서 시작 지점 역할을 하며 Apache 웹 서버와 통합된 Apache Tomcat이 포함되어 있습니다. Apache Software Foundation에서 Apache HTTP Server 2.4.53을 릴리스했습니다. 이 버전은 원격 공격자가 영향을 받는 시스템을 제어할 수 있는 취약점을 해결합니다. 추가 정보 [Apache 2.4.53 발표](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Adobe Campaign 팀은 다음 방법으로 Apache 버전 보안 업그레이드 활동을 수행합니다 **2022년 6월 15일** 이 Apache 취약성을 완화하고 인스턴스 환경을 보다 안전하게 만들기 위해. 이 업그레이드는 취약한 버전의 Apache HTTP Server에서 실행 중인 모든 Campaign Classic v7 Managed Services 고객, Campaign v8 및 Campaign Standard 고객에게 적용됩니다. 영향을 받은 경우 Adobe이 이미 연락하여 이 업그레이드에 대해 알려 주었습니다.

This upgrade is expected to run automatically outside of your normal business hours for you to continue using the Campaign service without any disruption.

비프로덕션 인스턴스가 먼저 Adobe으로 업그레이드되고 프로덕션 인스턴스가 업그레이드됩니다. Since this is an automatic upgrade process owned by Adobe, there is no action required from your side. 그러나 문제가 발생하는 경우 [고객 지원 Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>이 업그레이드를 수행하려면 Apache 웹 서버를 다시 시작해야 합니다. 다운타임은 아래에 언급된 시간 슬롯 내에서 10분을 초과하지 않습니다.

## FAQ(자주 묻는 질문) {#apache-faq}

* **이 업그레이드가 필수 업그레이드인 이유는 무엇입니까?**

   The current Apache version is vulnerable and has a potential security threat. It is important for your Campaign instance(s) to be upgraded to the latest applicable Apache version to address the security risk.

* **보안 업그레이드 대상 고객은 무엇입니까?**

   이전 Apache 버전에 구현된 Campaign 환경을 사용하는 모든 고객은 적용 가능한 최신 Apache 버전으로 업그레이드됩니다.

* **예상되는 다운타임은 무엇입니까?**

   The expected downtime is under 10 minutes.

* **고객이 이 보안 업그레이드를 위해 필요한 작업이 있습니까?**

   No actions is required since the security upgrade will run automatically.

* **유지 관리 기간 동안 실행 중인 캠페인/워크플로우는 어떤 영향을 줍니까?**

   유지 관리 기간 동안 워크플로우 및 메일 서비스가 모두 중지되며 예약된 활동이 실행되지 않습니다. 서버가 다시 시작될 때까지 가동 중지 시간 동안 진행 중인 모든 작업 또는 실행 프로세스가 중지됩니다. 활동이 완료되고 서버가 다시 시작되면 모든 서비스가 다시 시작됩니다.

* **고객이 실행해야 하는 유효성 검사**

   No specific testing is needed for this security upgrade. 문제가 확인되면 다음 주소로 문의하십시오 [고객 지원 Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **Can I request a change in Date/Time to the scheduled security upgrade slot?**

   보안 수정 사항이므로 기존 일정에 맞게 조정하는 것이 좋습니다.


For any other question, you can reach out to [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support).
