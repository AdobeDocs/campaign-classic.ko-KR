---
solution: Campaign Classic
product: campaign
title: 기술 문서
description: 기술 문서
hide: false
hidefromtoc: true
translation-type: tm+mt
source-git-commit: a21f970b6b81105517a11bcbd7f334173acc76e4
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Apple 푸시 알림 서비스 서버 인증서 업데이트 {#apns-certificate-update}

2021년 3월 29일에 APNs(Apple Push Notification 서비스) 인프라 업데이트는 Adobe Campaign Classic iOS 채널에 영향을 미칩니다. iOS 푸시 채널 중단을 방지하기 위해 OS 구성 변경은 **필수**&#x200B;입니다.

이 페이지](https://developer.apple.com/news/?id=7gx0a2lp)에서 APNs 변경 사항 [에 대해 자세히 알아보십시오.

호스팅 고객으로서 어떠한 작업도 필요하지 않습니다.Adobe에서 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객인 경우 **을 2021년 3월 29일 전에 원활하게 전환하도록 구성을 업데이트해야 합니다**.

새 인증서를 통합하려면 아래 절차를 따르십시오.

1. 이 페이지](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL)에서 **AACertificateServices 5/12/2020** 루트 인증서 [를 다운로드합니다.

1. OS Trust Store에 추가합니다.

1. Adobe Campaign 웹 서비스를 다시 시작합니다.

   ```
   nlserver restart web
   ```