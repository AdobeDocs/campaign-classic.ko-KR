---
title: 메시징 서버
seo-title: 메시징 서버
description: 메시징 서버
seo-description: null
page-status-flag: never-activated
uuid: d7de0405-23eb-4a0d-80a5-c75d661771bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1556e87f-9d92-4548-a75a-4f44030ab8d5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 메시징 서버{#messaging-server}

Adobe Campaign은 아웃바운드 이메일을 기본적으로 처리하지만 메일 메일 시스템 데몬에서 반환된 이메일에 연결된 수신 메시지를 수신해야 합니다. 이 서버에 구성된 사서함은 애플리케이션에서 자동으로 처리됩니다.

POP3 액세스에 대해 구성된 모든 서버는 메일을 선택할 때 SMTP &quot;Message-ID&quot; 헤더를 보존하는 경우 이메일을 받는 데 사용할 수 있습니다. 예를 들어 Qmail, SendMail 및 Microsoft Exchange를 사용하는 구현은 현재 제작 중입니다. 그러나 Lotus Notes/domino의 일부 설치에서는 &quot;Message-Id&quot; 헤더 유지 관리와 관련된 문제가 발견되었습니다.

>[!CAUTION]
>
>이 메일 서버는 많은 로드를 처리해야 할 수 있습니다.초기 단계에서 일반적인 목록은 최대 10%의 바운스 비율을 생성할 수 있습니다(100,000개의 메시지를 전송하는 경우 10,000개의 바운스 수가 예상됨).
>
>따라서 이 작업에 강력한 영향을 줄 수 있으므로 회사 메시징 서버를 사용하지 않는 것이 좋습니다.
>
>DNS의 특정 하위 도메인과 바운스 메일에 대한 전용 서버를 구성하는 것이 좋습니다.
