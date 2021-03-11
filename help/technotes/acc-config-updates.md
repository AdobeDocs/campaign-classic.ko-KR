---
solution: Campaign Classic
product: campaign
title: 기술 문서
description: 기술 문서
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 87844fae046dff69193d3462c802057499f406ef
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 5%

---


# Adobe Campaign 구성 업데이트 - 2021년 3월 {#acc-config-updates}

최신 빌드 및 제품 수정으로 인프라와 설정을 업데이트해야 합니다. 이러한 수정 사항은 서비스 연속성 및 보안을 보장하기 위해 반드시 필요합니다.

캠페인 사용자는 아래 최신 버전 중 하나로 업그레이드해야 합니다.

* Gold Standard 11. [자세히 알아보기](../rn/using/gold-standard.md)
* 캠페인 21.1.1 릴리스. [자세히 알아보기](../rn/using/latest-release.md)
* 캠페인 20.3.3 릴리스. [자세히 알아보기](../rn/using/release--20-3.md)
* 캠페인 20.2.4 릴리스. [자세히 알아보기](../rn/using/release--20-2.md)
* 캠페인 20.1.4 릴리스. [자세히 알아보기](../rn/using/release--20-1.md)
* 캠페인 19.2.4 릴리스. [자세히 알아보기](../rn/using/release--19-2.md)
* 캠페인 19.1.8 릴리스. [자세히 알아보기](../rn/using/release--19-1.md)

이러한 빌드는 특정 캠페인 서비스의 연속성을 보장합니다.Experience Cloud 트리거 통합, APNs 인증 및 Adobe Identity Management 서비스(IMS) 인증 메커니즘에 영향을 주는 새 연결 프로토콜.

호스팅 고객으로서 어떠한 작업도 필요하지 않습니다.Adobe은 사용자에 대한 빌드 업그레이드 및 구성 업데이트를 소유합니다.

온-프레미스/하이브리드 고객인 경우 위에 나열된 버전 중 하나로 업그레이드해야 합니다. 또한 Adobe 또는 제3자 시스템에서 변경될 수 있는 변경 사항에 대비하여 환경이 안전하고 준비되도록 몇 가지 수동 작업을 수행해야 합니다.

## 보안 업데이트

최신 캠페인 버전에는 SSRF(Server Side Request 위조) 문제에 대한 보호를 강화하는 보안 픽스가 포함되어 있습니다. 이 페이지](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)에서 [에 대해 자세히 알아보십시오.

**당신은 영향을 받습니까?**

환경이 Campaign 21.1보다 낮은 빌드에 있는 경우 영향을 받습니다.

**업데이트 방법**

위에 나열된 최신 빌드 중 하나로 업그레이드해야 합니다.

* 하이브리드 고객인 Adobe은 mid-sourcing 인스턴스를 새 버전으로 업그레이드하며 해당 마케팅 인스턴스도 업그레이드하는 것이 좋습니다.

   새 빌드는 최소 Campaign Classic 17.9 릴리스와 호환되지만 보안 간격을 방지하기 위해 모든 인스턴스를 새 빌드로 업그레이드할 것을 Adobe이 적극 권장합니다. 

* 온-프레미스 고객은 마케팅 및 mid 소싱 인스턴스를 새 빌드로 업그레이드하도록 요청됩니다.

>[!CAUTION]
>
>지금 업그레이드할 수 없는 경우 **Adobe 고객 지원 센터에 연락하여 인스턴스**&#x200B;에 대한 보안 픽스를 수동으로 적용해야 합니다.


## 캠페인 클라이언트 콘솔 업데이트

최신 Gold Standard 11 빌드는 배달에서 날짜 선택기 및 이미지 관리와 같은 콘솔의 일부 구성 요소를 사용할 수 없는 회귀 현상을 수정합니다. 콘솔 업그레이드는 필수입니다.

[자세히 알아보기](../rn/using/gold-standard.md)

## IMS를 통해 캠페인에 연결

IMS(Adobe Identity Service)는 2021년 6월 30일부터 이전 Internet Explorer 버전 지원을 중단할 예정입니다. [자세히 알아보기](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html) 캠페인 콘솔이 IMS와의 호환성을 보장하도록 업데이트되었습니다.

**당신은 영향을 받습니까?**

Adobe ID](../integrations/using/about-adobe-id.md)을 통해 IMS(Adobe ID 서비스)를 통해 캠페인 [에 연결하는 경우, 캠페인 서버와 클라이언트 콘솔 모두에서 2021년 6월 30일 이후 **Campaign에 연결할 수 있으려면 위에 나열된 새 버전 중 하나로 업그레이드해야 합니다.**

**업데이트 방법**

호스팅 고객으로서 어떠한 작업도 필요하지 않습니다.Adobe에서 이미 인스턴스를 새 버전으로 업그레이드했습니다.

온-프레미스/하이브리드 고객인 경우 새 클라이언트 콘솔의 혜택을 받고 2021년 3월 31일 이전 **으로 원활하게 전환하도록 하려면 최신 버전 중 하나로 업그레이드해야 합니다.**

## Experience Cloud 트리거과 통합

레거시 oAuth 인증 서비스가 사용이 중단되었습니다. 2021년 6월 30일에 종료됩니다. [자세히 알아보기](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

**당신은 영향을 받습니까?**

oAuth 인증을 통해 이전 버전의 트리거 통합을 사용하는 경우 **Adobe I/O**&#x200B;으로 이동해야 합니다.

**업데이트 방법**

[Adobe I/O으로 마이그레이션하는 방법을 알아봅니다](../integrations/using/configuring-adobe-io.md).

## HTTP/2 기반 APNs 공급자 API

2021년 3월 31일부로 Apple 푸시 알림 서비스(APNs)는 더 이상 레거시 이진 프로토콜을 지원하지 않습니다. [자세한 내용](https://developer.apple.com/kr/news/?id=c88acm2b).

**당신은 영향을 받습니까?**

인스턴스가 Campaign 21.1 이전 버전에서 실행되고 레거시 Apple 이진 프로토콜로 푸시 알림을 전송하는 경우 HTTP/2 기반 APNs 공급자 API로 업데이트해야 합니다.

**업데이트 방법**

호스팅 고객으로서 어떠한 작업도 필요하지 않습니다.Adobe에서 이미 인스턴스를 HTTP/2 기반 API로 업데이트했습니다.

온-프레미스/호스팅 고객인 경우 구성을 업데이트해야 합니다. [HTTP/2로 마이그레이션하는 방법 알아보기](https://helpx.adobe.com/kr/campaign/kb/migrate-to-apns-http2.html)

## APNs 루트 인증서 업데이트

2021년 3월 29일에 APNs(Apple Push Notification 서비스) 인프라 업데이트는 Adobe Campaign Classic iOS 채널에 영향을 미칩니다. iOS 푸시 채널 중단을 방지하기 위해 OS 구성 변경은 **필수**&#x200B;입니다.

이 페이지](https://developer.apple.com/news/?id=7gx0a2lp)에서 APNs 변경 사항 [에 대해 자세히 알아보십시오.

**당신은 영향을 받습니까?**

Campaign을 사용하여 iOS 장치에서 푸시 알림을 전송하는 경우 영향을 받습니다.

**업데이트 방법**

호스팅 고객으로서 어떠한 작업도 필요하지 않습니다.Adobe에서 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객인 경우 **을 2021년 3월 29일 전에 원활하게 전환하도록 구성을 업데이트해야 합니다**.

[새 인증서를 통합하는 방법 알아보기](ios-certificate-update.md)
