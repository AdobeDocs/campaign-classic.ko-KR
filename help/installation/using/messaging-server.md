---
product: campaign
title: 메시시 서버
description: 메시시 서버
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# 메시시 서버{#messaging-server}

![](../../assets/v7-only.svg)

Adobe Campaign은 아웃바운드 이메일을 기본적으로 처리하지만 반환 전자 메일(메일 데몬)에 연결된 수신 메시지를 수신하려면 기존 전자 메일 서버가 필요합니다. 이 서버에 구성된 사서함은 응용 프로그램에서 자동으로 처리됩니다.

POP3 액세스에 대해 구성된 모든 서버는 메일을 선택할 때 SMTP &quot;Message-ID&quot; 헤더를 유지하는 경우 반환 메일을 받는 데 사용할 수 있습니다. 예를 들어 Qmail, SendMail 및 Microsoft Exchange를 사용하는 구현은 현재 프로덕션 단계에 있습니다. 그러나 Lotus Notes/domino의 일부 설치에서는 &quot;Message-Id&quot; 헤더 유지 관련 문제를 해결했습니다.

>[!CAUTION]
>
>이 메일 서버는 많은 로드를 처리해야 할 수 있습니다. 초기 단계에서 일반적인 목록은 최대 10%의 바운스 비율을 생성할 수 있습니다(100,000개의 메시지를 전송하는 경우 10,000개의 바운스 수를 수신할 것).
>
>따라서 강력한 영향을 받을 수 있으므로 이 작업에 회사 메시징 서버를 사용하지 않는 것이 좋습니다.
>
>바운스 메일에 대한 DNS의 특정 하위 도메인과 전용 서버를 구성하는 것이 좋습니다.
