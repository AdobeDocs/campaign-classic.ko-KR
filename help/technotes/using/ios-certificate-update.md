---
product: campaign
title: 기술 정보 - Apple 푸시 알림 서비스 서버 인증서 업데이트
description: Apple 푸시 알림 서비스 서버 인증서 업데이트
feature: Technote, Push
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 0143e0d6ebcdbd96d183ddd0c7f07beb149a9670
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Apple 푸시 알림 서비스 서버 인증서 업데이트 {#apns-certificate-update}



2024년 10월 17일에 Apple APNs(푸시 알림 서비스) 인프라 업데이트로 Adobe Campaign Classic iOS 채널이 영향을 받았습니다. iOS 푸시 채널 중단을 방지하기 위해 OS 구성 변경은 **필수**&#x200B;입니다.

APNs 변경 사항에 대해 자세히 알아보세요[이 페이지에서](https://developer.apple.com/news/?id=09za8wzy).

호스팅된 고객은 별도의 작업이 필요하지 않습니다. Adobe은 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객은 **2025년 2월 24일 이전**&#x200B;에 원활하게 전환하도록 구성을 업데이트해야 합니다.

새 인증서를 통합하려면 아래 단계를 수행합니다.

1. **SHA-2 루트 : USERTrust RSA 인증 기관 인증서** 루트 인증서 [을(를) 이 페이지에서 다운로드하십시오](https://www.sectigo.com/knowledge-base/detail/Sectigo-Intermediate-Certificates/kA01N000000rfBO).

1. AAA 인증서가 OS와 JAVA Trustore 모두에 있는지 확인합니다. 그렇지 않으면 추가합니다.

1. Adobe Campaign 웹 서비스 다시 시작:

   ```
   nlserver restart web
   ```
