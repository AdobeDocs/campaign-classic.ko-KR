---
product: campaign
title: 기술 정보
description: 기술 정보
hide: true
hidefromtoc: true
source-git-commit: 53ac193211a1d98c45e97bf01ab0ad843b8f8f02
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 35%

---

# 추적된 URL 서명 문제 {#tracked-urls}

![](../../assets/v7-only.svg)

최근 변경 사항에 따라 Campaign에서 URL 서명이 활성 상태일 때 추적된 URL이 실패할 수 있습니다. 일부 회사에는 링크에 영향을 주고 URL 서명 메커니즘을 변경할 수 있는 특정 보안 도구가 있으므로 일부 사서함은 다른 사서함보다 더 큰 영향을 받을 수 있습니다.

따라서 Adobe은 링크 추적을 위해 서명 메커니즘을 비활성화하는 것이 좋습니다. 이 절차에서는 이중 이스케이프가 있는 링크를 제외한 이전 추적 링크를 수정합니다.

구독 취소 링크는 다른 모든 링크와 마찬가지로 실패할 수 있으며, 빈도는 호스트에 따라 다르지만 1% 미만입니다.

**영향을 받습니까?**

보안을 위해 이메일의 링크 추적을 위한 서명 메커니즘은 [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - 2020년 4월에 도입되었으며, 빌드 19.1.4(9032@3a9dc9c) 및 Campaign 20.2를 시작하는 모든 고객에 대해 기본적으로 활성화되어 있습니다.

환경이 아래 나열된 버전 중 하나에서 실행 중인 경우 영향을 받을 수 있습니다.

* Gold Standard 8~11. [자세히 알아보기](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1(빌드 9277)에서 21.1.2(빌드 9282) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/latest-release.md)
* Campaign 20.3.1(빌드 9228)에서 20.3.3(빌드 9234) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--20-3.md)
* Campaign 20.2.1(빌드 9178)에서 20.2.4(빌드 9187) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--20-2.md)
* Campaign 20.1.1(빌드 9122)에서 21.1.3(빌드 9124) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--20-1.md)
* Campaign 19.2.2(빌드 9080)에서 19.2.3(빌드 9081) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--19-2.md)
* Campaign 19.1.5(빌드 9033)에서 19.1.7(빌드 9036) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--19-1.md)

이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)에서 버전 [을 확인하는 방법을 알아봅니다.

**업데이트 방법**

호스팅된 **고객**&#x200B;으로서 Adobe이 귀사와 협력하여 구성을 곧 업데이트할 예정입니다.

**온-프레미스/하이브리드 고객**&#x200B;은 구성을 업데이트해야 합니다.

아래 단계를 따르십시오.

1. [서버 구성 파일](../../installation/using/the-server-configuration-file.md) (serverConf.xml)에서 **signEmailLinks**&#x200B;를 **false**&#x200B;로 변경합니다.
1. **nlserver** 서비스를 다시 시작합니다.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>**config-`<instance>`.xml** 파일은 **serverConf.xml** 설정을 무시합니다. **signEmailLinks**&#x200B;가 **config-`<instance>`.xml**(여기서 **instance**&#x200B;는 인스턴스 이름)에 있는 경우 **false**&#x200B;로도 설정해야 합니다.

**어떤 영향이 있습니까?**

유지 관리에는 최대 25분 다운타임이 필요하며 이 기간 동안 모든 게재, 추적 링크 및 API 호출이 작동하지 않습니다.

업데이트가 완료되면 모든 링크가 예상대로 작동합니다.

>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.