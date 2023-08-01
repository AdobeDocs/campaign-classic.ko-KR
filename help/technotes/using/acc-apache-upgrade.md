---
product: campaign
title: Technote - Adobe Campaign - Apache 버전 보안 업데이트
description: Adobe Campaign - Apache 버전 보안 업데이트
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 3d2f5d1d-4b31-4cc6-b6fb-13589856e00c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---

# Adobe Campaign - Apache 버전 보안 업데이트 {#apache-update}

>[!CAUTION]
>이 문서는 다음 경우에 적용됩니다. **Campaign Classic v7 Managed Services** 고객, **Campaign v8** 고객 및 **Campaign Standard** 고객.

Adobe Campaign은 타사 도구와 연동되며, 지원되는 버전만 구현하기 위해 호환성이 정기적으로 업데이트되고, 최신 수정 사항 및 개선 사항의 이점을 제공합니다.

Adobe Campaign에는 HTTP를 통해 애플리케이션 서버의 진입점 역할을 하며 Apache 웹 서버와 통합된 Apache Tomcat이 포함되어 있습니다. Apache Software Foundation에서 Apache HTTP Server 2.4.53을 발표했습니다. 이 버전은 원격 공격자가 영향을 받는 시스템을 제어할 수 있는 취약점을 해결합니다. 다음에서 자세히 알아보기 [Apache 2.4.53 발표](https://downloads.apache.org/httpd/Announcement2.4.html){target="_blank"}.

Adobe Campaign 팀은 다음을 수행하여 Apache 버전 보안 업그레이드 활동을 수행합니다. **2022년 6월 15일** 이 Apache 취약성을 완화하고 인스턴스 환경을 보다 안전하게 만듭니다. 이 업그레이드는 취약한 버전의 Apache HTTP Server에서 실행되는 모든 Campaign Classic v7 Managed Services 고객, Campaign v8 및 Campaign Standard 고객에게 적용됩니다. 영향을 받는 경우 이 업그레이드에 대해 알리기 위해 Adobe에서 이미 연락했습니다.

이 업그레이드는 정상 업무 시간 외에 자동으로 실행되므로 Campaign 서비스를 중단 없이 계속 사용할 수 있습니다.

비프로덕션 인스턴스는 Adobe에 의해 먼저 업그레이드된 다음 프로덕션 인스턴스가 업그레이드됩니다. 이는 Adobe이 소유한 자동 업그레이드 프로세스이므로 사용자 측에서 필요한 작업이 없습니다. 그러나 문제가 발생하는 경우 다음으로 문의하십시오. [Adobe 고객 지원 센터](https://experienceleague.adobe.com/?support-solution=Campaign#support).


>[!NOTE]
>이 업그레이드를 수행하려면 Apache 웹 서버를 다시 시작해야 합니다. 다운타임은 아래에 언급된 시간 슬롯 내에서 10분을 초과하지 않습니다.
> 

## FAQ(자주 묻는 질문) {#apache-faq}

* **필수 업그레이드인 이유는 무엇입니까?**

  현재 Apache 버전은 취약하며 잠재적인 보안 위협이 있습니다. 보안 위험을 해결하려면 Campaign 인스턴스를 적용 가능한 최신 Apache 버전으로 업그레이드해야 합니다.

* **보안 업그레이드의 대상이 되는 고객은 무엇입니까?**

  이전 Apache 버전에 구현된 Campaign 환경을 사용하는 모든 고객은 최신 적용 가능한 Apache 버전으로 업그레이드됩니다.

* **예상되는 다운타임은 무엇입니까?**

  예상되는 다운타임은 10분 미만입니다.

* **이 보안 업그레이드에 대해 고객이 수행해야 하는 작업이 있습니까?**

  보안 업그레이드가 자동으로 실행되므로 별도의 작업이 필요하지 않습니다.

* **유지 관리 기간 동안 실행 중인 캠페인/워크플로우에 미치는 영향은 무엇입니까?**

  유지 관리 기간 동안 워크플로우와 메일 서비스가 모두 중지되고 예약된 활동이 실행되지 않습니다. 서버가 다시 시작될 때까지 다운타임 동안 진행 중인 모든 작업 또는 실행 중인 프로세스가 중단됩니다. 활동이 완료되고 서버가 다시 시작되면 모든 서비스가 다시 시작됩니다.

* **고객이 실행해야 하는 유효성 검사는 무엇입니까?**

  이 보안 업그레이드에 특정 테스트가 필요하지 않습니다. 문제가 발생하는 경우 다음으로 문의하십시오. [Adobe 고객 지원 센터](https://experienceleague.adobe.com/?support-solution=Campaign#support).


* **예약된 보안 업그레이드 슬롯에 대한 날짜/시간 변경을 요청할 수 있습니까?**

  이는 보안 수정 사항이므로 기존 일정에 적응하는 것이 좋습니다.


기타 문의 사항은 다음으로 문의하십시오. [Adobe 고객 지원 센터](https://experienceleague.adobe.com/?support-solution=Campaign#support).
