---
product: campaign
title: 기술 정보 - Campaign 환경에서 Microsoft Edge Chromium 활성화
description: 캠페인 - Edge Chromium
feature: Technote, Upgrade
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
TQID: https://experienceleague.adobe.com/6CrzuBxAxGlXi08NxwdnigO2bNu700luLxnz-3KzZ18
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 274
ht-degree: 10%

---

# 환경에서 Microsoft Edge Chromium을 활성화하는 방법 {#edge-conf}

## 변경 사항

Microsoft Internet Explorer 11의 수명 종료에 따라 클라이언트 콘솔의 대시보드용 HTML 렌더링 엔진은 Campaign Classic v7.3부터 Edge Chromium을 사용합니다.

이제 [클라이언트 콘솔 설치에 필요](../../installation/using/installing-the-client-console.md#webview)인 Microsoft Edge Webview 2 런타임을 설치하는 것 외에, 인스턴스에서 Microsoft Edge Chromium을 활성화해야 합니다.

>[!NOTE]
>
>Microsoft Edge Chromium을 활성화한 후 브라우저의 검색 대화 상자를 여는 `Ctrl+F`(Windows) 또는 `Command+F`(Mac) 바로 가기가 더 이상 작동하지 않습니다.

## 영향을 받습니까?

환경이 Campaign Classic v7.3 이상으로 업그레이드된 경우 영향을 받습니다.

## 업데이트 방법

* **호스팅** 고객인 Adobe은 이미 인스턴스에서 Microsoft Edge Chromium을 활성화했습니다. 추가 작업은 필요하지 않습니다.

* **온-프레미스/하이브리드** 고객은 인스턴스에서 Microsoft Edge Chromium을 활성화해야 합니다.

  Campaign Classic v7.3 이상으로 업그레이드할 때 Campaign 서버 구성 파일 `serverConf.xml`에서 새 `webView2Mode` 특성을 사용할 수 있습니다. 이 특성을 활성화해야 합니다.

  이렇게 하려면 모든 환경(MKT, MID, RT)에 다음 단계를 적용합니다.

   1. Campaign 서버 구성 파일(`serverConf.xml`) 편집
   1. `<web>` 모듈에서 `webView2Mode = "1"` 설정
   1. 다음 명령을 실행하여 서버 구성을 다시 로드합니다.

      ```
      nlserver config -reload
      ```

   1. 다음 명령을 실행하여 웹 서버를 다시 시작합니다.

      ```
      nlserver restart web
      ```

   1. 사용자 환경에서 Apache를 웹 서버로 사용하는 경우 다음 명령을 실행하여 Apache를 다시 시작합니다.

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.
>

## 관련 항목

* [환경 업그레이드](../../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [Campaign 클라이언트 콘솔 설치](../../installation/using/installing-the-client-console.md)
