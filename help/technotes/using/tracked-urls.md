---
product: campaign
title: '추적된 URL 서명 문제 '
description: '추적된 URL 서명 문제 '
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 36%

---

# 추적된 URL 서명 문제 {#tracked-urls}

![](../../assets/v7-only.svg)

최근 변경 사항에 따라 Campaign에서 URL 서명이 활성 상태일 때 추적된 URL이 실패할 수 있습니다. 일부 회사에는 링크에 영향을 주고 URL 서명 메커니즘을 변경할 수 있는 특정 보안 도구가 있으므로 일부 사서함은 다른 사서함보다 더 큰 영향을 받을 수 있습니다.

따라서 Adobe은 링크 추적을 위해 서명 메커니즘을 비활성화하는 것이 좋습니다. 이 절차에서는 이중 이스케이프가 있는 링크를 제외한 이전 추적 링크를 수정합니다.

구독 취소 링크는 다른 모든 링크와 마찬가지로 실패할 수 있으며, 빈도는 호스트에 따라 다르지만 1% 미만입니다.

**영향을 받습니까?**

보안을 개선하기 위해 이메일의 링크를 추적하는 서명 메커니즘이 [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - 2020년 4월 - Build 19.1.4 (9032@3a9dc9c) 및 Campaign 20.2를 시작하는 모든 고객에 대해 기본적으로 활성화됩니다.

환경이 아래 나열된 버전 중 하나에서 실행 중인 경우 영향을 받을 수 있습니다.

* Gold Standard 8~11. [자세히 알아보기](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1(빌드 9277)에서 21.1.2(빌드 9282) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/latest-release.md)
* Campaign 20.3.1(빌드 9228)에서 20.3.3(빌드 9234) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--2020.md#release-20-3)
* Campaign 20.2.1(빌드 9178)에서 20.2.4(빌드 9187) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--2020.md#release-20-2)
* Campaign 20.1.1(빌드 9122)에서 21.1.3(빌드 9124) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--2020.md#release-20-1)
* Campaign 19.2.2(빌드 9080)에서 19.2.3(빌드 9081) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--2019.md#release-19-2)
* Campaign 19.1.5(빌드 9033)에서 19.1.7(빌드 9036) 릴리스로 이동합니다. [자세히 알아보기](../../rn/using/release--2019.md#release-19-1)


버전을 확인하는 방법을 알아봅니다 [이 섹션](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**업데이트 방법**

로서의 **호스팅 고객**, Adobe이 사용자와 협력하여 구성을 곧 업데이트할 예정입니다.

로서의 **온-프레미스/하이브리드 고객**&#x200B;를 눌러 구성을 업데이트해야 합니다.

아래 단계를 따르십시오.

1. 에서 [서버 구성 파일](../../installation/using/the-server-configuration-file.md) (serverConf.xml), 변경 **signEmailLinks** to **false**.
1. 를 다시 시작합니다. **nlserver** 서비스.
1. 추적 서버에서 웹 서버(Debian의 apache2, CentOS/RedHat의 httpd, Windows의 IIS)를 다시 시작합니다.

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>다음 **config-`<instance>`.xml** 파일이 를 재정의합니다. **serverConf.xml** 설정. 만약 **signEmailLinks** 에 있음  **config-`<instance>`.xml** (다음과 같은 경우) **인스턴스** 는 인스턴스의 이름임)이며, **false**.

**어떤 영향이 있습니까?**

유지 관리에는 최대 25분 다운타임이 필요하며 이 기간 동안 모든 게재, 추적 링크 및 API 호출이 작동하지 않습니다.

업데이트가 완료되면 모든 링크가 예상대로 작동합니다.

>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.
