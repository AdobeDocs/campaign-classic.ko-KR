---
title: 트랜잭션 메시지 기본 정보
description: '정보 시스템에서 생성된 이벤트를 기반으로 트리거 메시지를 전송할 수 있습니다. '
page-status-flag: never-activated
uuid: c854daac-8756-44f3-a4e2-be31177ab9d1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: 97df4bd5-a8e3-48f4-87c8-fa090ea3f771
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: eccf0e9899426c2517748c7a72611ff098291cd2
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---


# 트랜잭션 메시지 기본 정보{#about-transactional-messaging}

트랜잭션 메시지(메시지 센터)는 트리거 메시지 관리를 위해 설계된 캠페인 모듈입니다. 이러한 메시지는 정보 시스템에서 트리거된 이벤트에서 생성되며 다음과 같은 작업을 수행할 수 있습니다.송장, 주문 확인, 배송 확인, 암호 변경, 제품 미가용성 통지, 계정 명세서 또는 웹사이트 계정 생성 등의 작업을 들 수 있습니다.

>[!IMPORTANT]
>
>트랜잭션 메시징에는 특정 라이선스가 필요합니다. 사용권 계약을 확인하십시오.

Adobe Campaign 메시지 센터 모듈은 개인화된 트랜잭션 메시지로 변경할 이벤트를 반환하는 정보 시스템에 통합됩니다. 이러한 메시지는 이메일, SMS 또는 푸시 알림을 통해 개별적으로 또는 일괄적으로 보낼 수 있습니다.

이 특정 아키텍처에서는 실행 셀이 제어 인스턴스와 분리되어 더 높은 가용성 및 더 나은 로드 관리를 보장합니다.

>[!NOTE]
>
>Adobe Cloud에서 호스팅되는 메시지 센터 실행 인스턴스용 새 사용자를 만들려면 Adobe 고객 지원 센터에 문의해야 합니다. 메시지 센터 사용자는 &#39;실시간 이벤트&#39;(nmsRtEvent) 폴더에 액세스하기 위한 전용 권한이 필요한 특정 연산자입니다.
