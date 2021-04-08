---
solution: Campaign Classic
product: campaign
title: 기술 문서
description: 기술 문서
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 8%

---

# Adobe Campaign 구성 업데이트 - 2021년 3월 {#acc-config-updates}

인프라 및 설정은 최신 빌드 및 제품 수정을 통해 정기적으로 업데이트해야 합니다. 이러한 수정 사항은 서비스 및 보안을 지속하기 위해 필요합니다. 또한 타사 변경 사항에 맞게 업그레이드해야 합니다.

**호스팅 또는 Managed Services 고객**&#x200B;인 Adobe은 정기적으로 빌드 업그레이드를 알려줍니다. 규정을 준수하려면 권장 사항에 따라 업그레이드해야 합니다.

**온-프레미스 또는 하이브리드 고객**&#x200B;인 경우 최근에 릴리스된 빌드에 따라 정기적으로 구현을 업그레이드해야 합니다.

보안상의 이유로 이제 아래 나열된 버전 중 하나로 업그레이드해야 합니다. 표준 업그레이드 단계 외에, Adobe 또는 제3자 시스템의 향후 변경 사항에 맞게 환경이 안전하고 준비되도록 몇 가지 수동 작업을 수행해야 합니다.

>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.


## 보안 업데이트 {#acc-security-updates}

최신 캠페인 버전에는 SSRF(Server Side Request 위조) 문제에 대한 보호를 강화하는 보안 픽스가 포함되어 있습니다. 이 페이지](https://helpx.adobe.com/kr/security/products/campaign/apsb21-04.html)에서 [에 대해 자세히 알아보십시오.

**당신은 영향을 받습니까?**

환경이 아래 나열된 것보다 낮은 빌드에 있는 경우 영향을 받습니다.

* Gold Standard 11. [자세히 알아보기](../rn/using/gold-standard.md)
* 캠페인 21.1.1 릴리스. [자세히 알아보기](../rn/using/latest-release.md)
* 캠페인 20.3.3 릴리스. [자세히 알아보기](../rn/using/release--20-3.md)
* 캠페인 20.2.4 릴리스. [자세히 알아보기](../rn/using/release--20-2.md)
* 캠페인 20.1.4 릴리스. [자세히 알아보기](../rn/using/release--20-1.md)
* 캠페인 19.2.4 릴리스. [자세히 알아보기](../rn/using/release--19-2.md)
* 캠페인 19.1.8 릴리스. [자세히 알아보기](../rn/using/release--19-1.md)

이 섹션](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 버전 [을 확인하는 방법을 알아봅니다.

**업데이트 방법**

위에 나열된 최신 빌드 중 하나로 업그레이드해야 합니다.

* 하이브리드 고객인 Adobe은 중간 소싱 인스턴스에 대한 예약 업그레이드 날짜를 알려줍니다. Adobe은 마케팅 인스턴스도 업그레이드할 것을 적극 권장합니다.

   새 빌드는 Campaign Classic 17.9 릴리스와 역호환되지만 Adobe은 보안 취약점을 해결하기 위해 모든 인스턴스에서 업그레이드할 것을 적극 권장합니다

* 온-프레미스 고객은 마케팅 및 mid 소싱 인스턴스를 최신 빌드로 업그레이드하도록 요청됩니다.

>[!CAUTION]
>
>권장 기간 내에 업그레이드할 수 없는 경우 **Adobe 고객 지원 센터에 문의하여 인스턴스**&#x200B;에 대해 단기 수동 보안 픽스를 적용해야 합니다.


## Campaign Classic 클라이언트 콘솔 업데이트 {#acc-cc-updates}

최근에 식별된 회귀를 해결하려면 아래 **현재 사용 가능한** 콘솔 버전을 설치해야 합니다. 이 회귀로 인해 배달에서 날짜 선택기 및 이미지 관리와 같은 클라이언트 콘솔의 일부 구성 요소가 사용되지 않았습니다. **콘솔** 업그레이드는 필수입니다.

* 최신 Gold Standard 11 빌드는 9032@10c2709입니다. [자세히 알아보기](../rn/using/gold-standard.md)
* 캠페인 20.1.4 릴리스. [자세히 알아보기](../rn/using/release--20-1.md)
* 캠페인 19.2.4 릴리스. [자세히 알아보기](../rn/using/release--19-2.md)
* 캠페인 19.1.8 릴리스. [자세히 알아보기](../rn/using/release--19-1.md)

## Adobe Identity Management 시스템(IMS) 업데이트

IMS(Adobe Identity Service)는 2021년 6월 30일부터 이전 Internet Explorer 버전 지원을 중단합니다&#x200B;**.** [자세히 알아보기](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Adobe IMS와 호환되도록 하려면 캠페인 클라이언트 콘솔을 업그레이드해야 합니다.

**당신은 영향을 받습니까?**

Adobe ID](../integrations/using/about-adobe-id.md)을 통해 IMS(Identity Management Service)를 통해 캠페인 [에 연결하는 경우 아래 나열된 새 버전 중 하나로 업그레이드해야 합니다.

* Gold Standard 11. [자세히 알아보기](../rn/using/gold-standard.md)
* 캠페인 21.1.1 릴리스. [자세히 알아보기](../rn/using/latest-release.md)
* 캠페인 20.3.3 릴리스. [자세히 알아보기](../rn/using/release--20-3.md)
* 캠페인 20.2.4 릴리스. [자세히 알아보기](../rn/using/release--20-2.md)
* 캠페인 20.1.4 릴리스. [자세히 알아보기](../rn/using/release--20-1.md)
* 캠페인 19.2.4 릴리스. [자세히 알아보기](../rn/using/release--19-2.md)
* 캠페인 19.1.8 릴리스. [자세히 알아보기](../rn/using/release--19-1.md)

이러한 릴리스는 새 연결 프로토콜과 함께 제공됩니다.**2021년 6월 30일 이후 캠페인 서버와 클라이언트 콘솔 모두에서 캠페인에 연결할 수 있으려면 업그레이드가 필요합니다**.

이 섹션](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 버전 [을 확인하는 방법을 알아봅니다.

**업데이트 방법**

호스팅된 고객인 Adobe은 인스턴스를 최신 버전으로 업그레이드하기 위해 고객과 함께 작업합니다.

온-프레미스/하이브리드 고객인 경우 새 클라이언트 콘솔의 혜택을 받고 2021년 6월 30일 이전 **으로 원활하게 전환하도록 하려면 최신 버전 중 하나로 업그레이드해야 합니다.**

모든 인스턴스가 업그레이드되면 클라이언트 콘솔도 이 버전으로 업그레이드해야 합니다.

* [Adobe 소프트웨어 배포](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)에 액세스하는 방법을 알아봅니다.

* [캠페인 클라이언트 콘솔 설치 방법에 대해 알아봅니다](../installation/using/installing-the-client-console.md).

## Experience Cloud 트리거 {#acc-triggers-updates}와의 통합

레거시 oAuth 인증 서비스가 사용 종료되었습니다. 원래 oAUTH 인증 설정을 기반으로 파이프라인에 액세스하는 통합 인증이 Adobe I/O으로 이동되었습니다.**2021년 11월 30일에 종료됩니다**. [자세히 알아보기](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email)

**당신은 영향을 받습니까?**

인스턴스가 캠페인 19.1.8, 20.2.4, Gold Standard 11 **보다 이전 버전에서 실행 중인 경우, 이전 버전의 트리거 통합을 oAuth 인증을 통해 사용하고 있습니다.**&#x200B;새 버전으로 업그레이드하고 Adobe I/O **으로 이동해야 합니다.**

아래 나열된 새 버전 중 하나로 업그레이드해야 합니다.

* Gold Standard 11. [자세히 알아보기](../rn/using/gold-standard.md)
* 캠페인 21.1.1 릴리스. [자세히 알아보기](../rn/using/latest-release.md)
* 캠페인 20.2.5 릴리스. [자세히 알아보기](../rn/using/release--20-2.md)
* 캠페인 19.1.8 릴리스. [자세히 알아보기](../rn/using/release--19-1.md)

이 섹션](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 버전 [을 확인하는 방법을 알아봅니다.

**업데이트 방법**

인스턴스가 새 버전으로 업그레이드되면 모든 고객은 [절차를 따라 새 인증 모드](../integrations/using/configuring-adobe-io.md)로 이동해야 합니다. 이를 위해서는 새 Adobe I/O 토큰을 생성하여 구현에서 사용해야 합니다.  

또한 하이브리드 환경의 경우 고객은 mid-sourcing 인스턴스에 파이프라인이 구성되어 있는지 확인해야 합니다. [자세히 알아보기](../integrations/using/configuring-pipeline.md)

[Adobe I/O으로 마이그레이션하는 방법을 알아봅니다](../integrations/using/configuring-adobe-io.md).

## APNs 업데이트 {#acc-apns-updates}

### HTTP/2 기반 APNs 공급자 API

**2021년 3월 31일부터 APNs(Apple Push Notification service)는 더 이상 레거시 이진 프로토콜을 지원하지 않습니다.** [자세한 내용](https://developer.apple.com/kr/news/?id=c88acm2b).

**당신은 영향을 받습니까?**

인스턴스가 Campaign 21.1,**보다 이전 버전에서 실행 중이며, 레거시 Apple 이진 프로토콜을 사용하여 푸시 알림을 전송하는 경우, HTTP/2 기반 APNs 공급자 API로 업데이트해야 합니다.**

이 섹션](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 버전 [을 확인하는 방법을 알아봅니다.

**업데이트 방법**

호스팅된 고객인 경우 새 빌드로 업그레이드한 경우 Adobe은 이미 인스턴스를 HTTP/2 기반 API로 업데이트했습니다.

온-프레미스/하이브리드 고객인 경우 구성을 업데이트해야 합니다. [HTTP/2로 마이그레이션하는 방법 알아보기](https://helpx.adobe.com/kr/campaign/kb/migrate-to-apns-http2.html)

### APNs 루트 인증서 업데이트

2021년 3월 29일, APNs(Apple Push Notification 서비스) 인프라 업데이트는 Adobe Campaign Classic iOS 채널에 영향을 주었습니다. iOS 푸시 채널 중단을 방지하기 위해 OS 구성 변경은 **필수**&#x200B;입니다.

이 페이지](https://developer.apple.com/news/?id=7gx0a2lp)에서 APNs 변경 사항 [에 대해 자세히 알아보십시오.

**당신은 영향을 받습니까?**

Campaign을 사용하여 iOS 장치에서 푸시 알림을 전송하는 경우 영향을 받습니다.

**업데이트 방법**

호스팅 고객으로서 어떠한 작업도 필요하지 않습니다.Adobe에서 이미 새 루트 인증서를 환경에 통합했습니다.

온-프레미스/하이브리드 고객인 경우 **을 2021년 3월 29일 전에 원활하게 전환하도록 구성을 업데이트해야 합니다**.

[새 인증서를 통합하는 방법을 알아봅니다](ios-certificate-update.md).

## 유용한 링크

* [환경 업그레이드](../production/using/build-upgrade.md)
* [업그레이드 FAQ 빌드](../platform/using/faq-build-upgrade.md)
* [Campaign Classic 빌드 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [사용자가 새 클라이언트 콘솔을 사용할 수 있도록 설정](../installation/using/client-console-availability-for-windows.md)
