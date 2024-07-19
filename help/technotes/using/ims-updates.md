---
product: campaign
title: 기술 정보 - IMS를 사용하여 Adobe Campaign에 연결하도록 환경 업데이트
description: Campaign - IMS 업데이트
feature: Technote, Upgrade
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 5%

---

# IMS를 사용하여 Adobe Campaign에 연결하기 위해 환경을 업데이트하는 방법 {#acc-ims-faq}



2021년 6월 30일부터 Adobe Campaign을 계속 사용할 수 있는 기능에 영향을 줄 수 있는 [IMS(Identity Management System](https://helpx.adobe.com/kr/enterprise/using/identity.html)) Adobe 로그인 기능이 변경되었습니다. 중단 없이 Adobe Campaign Classic v7을 계속 사용하는 방법을 알아봅니다.

## 변경 사항

IMS(Adobe Identity Management 서비스)가 **2021년 6월 30일**&#x200B;에 이전 Internet Explorer 버전 지원을 중지했습니다. [자세히 알아보기](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html).

Adobe이 2021년 6월 30일 이전의 모든 고객을 위해 IMS 기능을 유지하려고 합니다. IMS는 사용자가 클라이언트 콘솔에 로그인할 수 있도록 하는 보안 프레임워크의 일부입니다. 따라서 Adobe Campaign입니다.

이 기능을 유지하려면 고객은 각 사용자의 컴퓨터에서 클라이언트 콘솔을 업데이트하고 **Internet Explorer 11**&#x200B;이(가) 내장된 [Windows 버전](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)의 최신 업데이트가 각 사용자의 컴퓨터에 설치되어 있는지 확인해야 합니다.

## 영향을 받습니까?

Adobe ID을 통해 [IMS(Identity Management 서비스) Adobe을 통해 ](../../integrations/using/about-adobe-id.md) Campaign에 연결하고 아래 나열된 버전보다 이전 버전의 Campaign을 실행하는 경우 영향을 받습니다.

이미 업그레이드했지만 이전 버전의 Microsoft Internet Explorer를 사용하는 경우 Internet Explorer 11로 업그레이드해야 합니다.

## 업데이트 방법

* 호스팅된 Adobe은 이미 인스턴스를 최신 버전으로 업그레이드했습니다.

* 온-프레미스/하이브리드 고객은 위에 나열된 최신 버전 중 하나로 업그레이드해야 새 클라이언트 콘솔의 혜택을 받고 원활한 전환을 **2021년 6월 30일 이전**&#x200B;해야 합니다.

  아래 나열된 새 버전 중 하나로 업그레이드해야 합니다.

   * Gold Standard 11. [자세히 알아보기](../../rn/using/gold-standard.md)
   * Campaign 21.1.3 릴리스 [자세히 알아보기](../../rn/using/latest-release.md)
   * Campaign 20.2.5 릴리스
   * Campaign 20.1.4 릴리스
   * Campaign 19.2.4 릴리스

  이러한 릴리스는 새 연결 프로토콜과 함께 제공됩니다. Campaign 서버와 클라이언트 콘솔은 모두 업그레이드해야 합니다. 모든 인스턴스가 업그레이드되면 **2021년 6월 30일** 이후에 Campaign에 연결할 수 있도록 클라이언트 콘솔도 이 버전으로 업그레이드해야 합니다.

또한 **Internet Explorer 11**&#x200B;가 내장된 [Windows 버전](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)의 최신 업데이트가 각 사용자의 컴퓨터에 설치되어 있는지 확인하십시오.

## FAQ

**Campaign 버전을 확인하려면 어떻게 해야 합니까?**

이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 사용 중인 버전 [을(를) 확인하는 방법을 알아보세요.


**IMS를 사용하는지 어떻게 확인할 수 있습니까?**

연결 모드를 확인하려면 다음을 수행할 수 있습니다.

* Campaign 클라이언트 콘솔을 실행하고 인스턴스 연결 설정에 액세스합니다. **Adobe ID과 연결** 옵션을 선택한 경우 Adobe IMS를 사용하고 있습니다.

  ![](../../integrations/using/assets/ims_1.png)

또는

* Campaign 클라이언트 콘솔을 실행하고 연결 창을 확인하십시오. 아래 화면에 표시된 대로 Adobe ID으로 연결하는 경우 IMS를 사용합니다.

  ![](../../integrations/using/assets/adobeID.png)

**연결 경고 메시지**

사용자가 클라이언트 콘솔을 업데이트하거나 이전 버전의 Microsoft Internet Explorer를 사용해야 하는 경우 다음 경고 메시지가 표시됩니다. **Windows 및/또는 Adobe 앱에 대한 최신 업데이트를 설치해야 합니다.**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

이러한 경고가 표시되면 사용 중인 운영 체제의 최신 업데이트를 설치해야 합니다. [자세히 알아보기](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

Internet Explorer 버전을 업데이트하지 않으면 다음 메시지가 표시되어 더 이상 Adobe Campaign에 연결할 수 없습니다.

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.
>

## 유용한 링크

* [환경 업그레이드](../../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [사용자가 새 클라이언트 콘솔을 사용할 수 있도록 설정](../../installation/using/client-console-availability-for-windows.md)
* [Campaign 클라이언트 콘솔 설치](../../installation/using/installing-the-client-console.md)
* [Adobe 소프트웨어 배포 액세스](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko)
* [Campaign Classic 빌드 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html)
