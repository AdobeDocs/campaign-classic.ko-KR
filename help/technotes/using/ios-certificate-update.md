---
product: campaign
title: 기술 정보 - Apple 푸시 알림 서비스 서버 인증서 업데이트
description: Apple 푸시 알림 서비스 서버 인증서 업데이트
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 263fb4b5-ca62-4b92-a82d-8820ee998296
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Apple 푸시 알림 서비스 서버 인증서 업데이트 {#apns-certificate-update}



2021년 3월 29일 Apple APNs(푸시 알림 서비스) 인프라 업데이트로 Adobe Campaign Classic iOS 채널이 영향을 받았습니다. OS 구성 변경은 **필수** iOS 푸시 채널 중단을 방지합니다.

APNs 변경 사항에 대해 자세히 알아보기 [이 페이지에서](https://developer.apple.com/news/?id=7gx0a2lp).

호스팅된 고객은 별도의 작업이 필요하지 않습니다. Adobe은 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객은 원활한 전환을 위해 구성을 업데이트해야 합니다 **2021년 3월 29일 이전**.

새 인증서를 통합하려면 아래 단계를 수행합니다.

1. 다운로드 **AACertificateServices 2020년 5월 12일** 루트 인증서 [이 페이지에서](https://support.sectigo.com/Com_KnowledgeDetailPage?Id=kA03l00000117cL).

1. AAA 인증서가 OS와 JAVA Trustore 모두에 있는지 확인합니다. 그렇지 않으면 추가합니다.

1. Adobe Campaign 웹 서비스 다시 시작:

   ```
   nlserver restart web
   ```
