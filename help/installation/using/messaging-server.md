---
product: campaign
title: 메시시 서버
description: 메시시 서버
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: d9ffa58d-81e3-4291-8502-3cb7c326b666
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 3%

---

# 메시시 서버{#messaging-server}



Adobe Campaign은 기본적으로 아웃바운드 이메일을 처리하지만 반환된 이메일에 연결된 수신 메시지를 수신하려면 기존 이메일 서버가 필요합니다(mailer 데몬에서). 이 서버에 구성된 사서함은 응용 프로그램에서 자동으로 처리됩니다.

메일을 선택할 때 SMTP &quot;Message-ID&quot; 헤더를 유지하는 경우 POP3 액세스용으로 구성된 모든 서버를 사용하여 반환 메일을 받을 수 있습니다. 예를 들어 Qmail, SendMail 및 Microsoft Exchange를 사용하는 구현은 현재 프로덕션에 있습니다. 그러나 Lotus Notes/domino의 일부 설치에서 &quot;Message-Id&quot; 헤더 유지 관리에 문제가 있었습니다.

>[!CAUTION]
>
>이 메일 서버는 많은 로드를 처리해야 할 수 있습니다. 초기 단계에서 일반적인 목록은 최대 10%의 바운스 비율을 생성할 수 있습니다(100,000개의 메시지를 보내는 경우 10,000개의 바운스를 받을 것으로 예상).
>
>따라서 이 작업은 영향을 크게 받을 수 있으므로 회사 메시징 서버를 사용하지 않는 것이 좋습니다.
>
>바운스 메일용 DNS 및 전용 서버의 특정 하위 도메인을 구성하는 것이 좋습니다.
