---
title: 기술 모니터링
seo-title: 기술 모니터링
description: 기술 모니터링
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# 기술 모니터링{#technical-monitoring}

## 기술 제공 모니터링 보고서 {#technical-deliverability-monitoring}

기술 제공 모니터링 보고서는 매일 업데이트되며 **[!UICONTROL Monitoring]** > **[!UICONTROL Overview]** 으로 이동하고 Adobe Campaign **[!UICONTROL Technical monitoring]** 탭에서 **[!UICONTROL Home]** 링크를 클릭하여 사용할 수 있습니다. 플랫폼용 전달 품질 지표가 포함되어 있습니다.

이러한 지표는 매일 오전 9시에 업데이트됩니다.

>[!NOTE]
>
>또한 지정된 주소로 일일 보고서를 이메일로 받을 수 있습니다. 이메일 또는 Adobe Campaign Extranet을 통해 요청된 이메일 주소를 알려주십시오.

![](assets/s_tn_del_monitoring.png)

보고서에서 사용되는 지표는 다음과 같습니다.

* **[!UICONTROL Reverse DNS]** :Adobe Campaign은 역 DNS가 IP 주소를 지정했는지 여부와 이 IP를 정확히 가리키는지 확인합니다.

* **[!UICONTROL SPF]** (발신자 정책 프레임워크):ISP 및 사서함 공급자가 이메일 보낸 사람이 송신 도메인에서 인증되었는지 확인할 수 있도록 하는 인증 메커니즘입니다.

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** :Yahoo가 개발한 서비스로, 이메일 발신자의 신원을 인증합니다.

* **[!UICONTROL IP and RBL domain]** (실시간 블랙홀 목록):잘못된 전송 평판을 위해 blocklist 조직에서 플래그를 지정한 IP 주소 및 도메인 목록입니다. 이러한 목록은 Spamhaus, Spamcop, SURBL/URIBL 등과 같은 전담 조직이 유지 관리합니다. Adobe Campaign은 현재 RBL에 대한 검사를 처리하며, 이러한 RBL은 전달에 상당한 영향을 줍니다. 이러한 RBL은 전송 명성을 반영하며, 이메일을 받기 위해 수락하기 전에 ISP에서 참조할 수 있습니다.

* **[!UICONTROL SNDS]** (스마트 네트워크 데이터 서비스):Windows [Live Hotmail 스팸 방지 서비스](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx). Hotmail은 이러한 유형의 정보를 제공하는 유일한 ISP입니다. 벤치마크 점수는 녹색 필터 결과, 불만 비율이 0.1% 미만이고 스팸 트랩이 0입니다.

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
