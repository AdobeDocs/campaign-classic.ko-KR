---
product: campaign
title: 기술 정보 - Apple 푸시 알림 서비스 서버 인증서 업데이트
description: Apple 푸시 알림 서비스 서버 인증서 업데이트
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0c97efef21bfd3b8671847c3e1c27bb76cf167e4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Apple 푸시 알림 서비스 서버 인증서 업데이트 {#apns-certificate-update}

![](../../assets/v7-only.svg)

2021년 3월 29일, APNs(Apple 푸시 알림 서비스) 인프라 업데이트는 Adobe Campaign Classic iOS 채널에 영향을 주었습니다. OS 구성 변경은 다음과 같습니다 **필수** iOS 푸시 채널 중단을 방지하려면

APNs 변경 사항에 대해 자세히 알아보기 [이 페이지에서](https://developer.apple.com/news/?id=7gx0a2lp).

호스팅된 고객으로서 아무 작업도 필요하지 않습니다. Adobe이 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객은 원활한 전환을 위해 구성을 업데이트해야 합니다 **2021년 3월 29일 이전**.

새 인증서를 통합하려면 아래 단계를 수행하십시오.

1. 다운로드 **AACertificateServices 5/12/2020** 루트 인증서 [이 페이지에서](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. OS 및 JAVA Trustore 모두에 AAA 인증서가 있는지 확인합니다. 없는 경우 추가합니다.

1. Adobe Campaign 웹 서비스를 다시 시작합니다.

   ```
   nlserver restart web
   ```
