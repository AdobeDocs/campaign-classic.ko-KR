---
product: campaign
title: 기술 정보
description: 기술 정보
hide: false
hidefromtoc: true
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Apple 푸시 알림 서비스 서버 인증서 업데이트 {#apns-certificate-update}

![](../../assets/v7-only.svg)

2021년 3월 29일에 APNs(Apple Push Notification service) 인프라 업데이트가 Adobe Campaign Classic iOS 채널에 영향을 줍니다. OS 구성 변경은 iOS 푸시 채널 중단을 방지하기 위해 **필수**&#x200B;입니다.

APNs 변경 사항 [에 대해 이 페이지에서 자세히 알아보십시오](https://developer.apple.com/news/?id=7gx0a2lp).

호스팅된 고객으로서 아무 작업도 필요하지 않습니다. Adobe이 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객은 2021년 3월 29일 전에 **이 원활하게 전환되도록 구성을 업데이트해야 합니다.**

새 인증서를 통합하려면 아래 단계를 수행하십시오.

1. 이 페이지에서 **AACertificateServices 5/12/2020** 루트 인증서 [를 다운로드하십시오.](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)

1. OS 및 JAVA Trustore 모두에 AAA 인증서가 있는지 확인합니다. 없는 경우 추가합니다.

1. Adobe Campaign 웹 서비스를 다시 시작합니다.

   ```
   nlserver restart web
   ```
