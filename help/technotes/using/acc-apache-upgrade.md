---
product: campaign
title: 기술 정보 - Adobe Campaign - Apache 버전 보안 업데이트
description: Adobe Campaign - Apache 버전 보안 업데이트
hide: true
hidefromtoc: true
source-git-commit: 41aa16e3ac6f150b9a048a22729b4cc4b9ccc10a
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Adobe Campaign - Apache 버전 보안 업데이트 {#apache-update}

Campaign Classic은 타사 도구와 연동되며, 호환성은 지원되는 버전만 구현하고 최신 수정 및 개선 사항을 활용할 수 있도록 정기적으로 업데이트됩니다.

Adobe Campaign에는 HTTP를 통해 애플리케이션 서버에서 시작 지점 역할을 하며 Apache 웹 서버와 통합된 Apache Tomcat이 포함되어 있습니다. Apache Software Foundation에서 Apache HTTP Server 2.4.53을 릴리스했습니다. 이 버전은 원격 공격자가 영향을 받는 시스템을 제어할 수 있는 취약점을 해결합니다. 추가 정보 [Apache 2.4.53 발표](https://downloads.apache.org/httpd/Announcement2.4.html){target=&quot;_blank&quot;}.

Adobe Campaign 팀은 다음 방법으로 Apache 버전 보안 업그레이드 활동을 수행합니다 **2022년 5월 31일** 이 Apache 취약성을 완화하고 인스턴스 환경을 보다 안전하게 만들기 위해. 이 업그레이드는 취약한 버전의 Apache HTTP Server에서 실행 중인 모든 Managed Services 고객에게 적용됩니다. 영향을 받은 경우 Adobe이 이미 연락하여 이 업그레이드에 대해 알려 주었습니다.

이 업그레이드는 중단 없이 Campaign 서비스를 계속 사용할 수 있도록 일반 영업시간 외부에서 자동으로 실행됩니다.

프로덕션 인스턴스를 업그레이드하기 전에 먼저 팀에서 비프로덕션 인스턴스를 업그레이드합니다. 이 프로세스는 Adobe이 소유한 자동 업그레이드 프로세스이므로 고객측에서 수행할 필요가 없습니다. 그러나 문제가 발생하는 경우 [고객 지원 Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>이 업그레이드를 수행하려면 Apache 웹 서버를 다시 시작해야 합니다. 다운타임은 아래에 언급된 시간 슬롯 내에서 10분을 초과하지 않습니다.

## FAQ(자주 묻는 질문) {#apache-faq}

* **이 업그레이드가 필수 업그레이드인 이유는 무엇입니까?**

   현재 Apache 버전은 취약하며 잠재적인 보안 위협을 가지고 있습니다. 보안 위험을 해결하기 위해 Campaign 인스턴스를 적용 가능한 최신 Apache 버전으로 업그레이드해야 합니다.


* **보안 업그레이드 대상 고객은 무엇입니까?**

   이전 Apache 버전에 구현된 Campaign 환경을 사용하는 모든 고객은 적용 가능한 최신 Apache 버전으로 업그레이드됩니다.

* **예상되는 다운타임은 무엇입니까?**

   예상 다운타임이 10분 미만입니다.


* **고객이 이 보안 업그레이드를 위해 필요한 작업이 있습니까?**

   보안 업그레이드가 자동으로 실행되므로 작업이 필요하지 않습니다.


* **고객이 실행해야 하는 유효성 검사**

   이 보안 업그레이드에 특정 테스트가 필요하지 않습니다. 문제가 확인되면 다음 주소로 문의하십시오 [고객 지원 Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support)


* **예약된 보안 업그레이드 슬롯의 날짜/시간 변경을 요청할 수 있습니까?**

   보안 수정 사항이므로 기존 일정에 맞게 조정하는 것이 좋습니다.


다른 문의 사항은 [고객 지원 Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).
