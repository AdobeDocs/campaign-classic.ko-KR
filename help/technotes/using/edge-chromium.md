---
product: campaign
title: 기술 정보 - Campaign 환경에서 Microsoft Edge Chromium 활성화
description: Campaign - Edge Chromium
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 095919608e08a0bf8ad1487fa5ec0a1ddb443c7b
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---

# 환경에서 Microsoft Edge Chromium을 활성화하는 방법 {#edge-conf}

![](../../assets/v7-only.svg)


## 변경 사항

Microsoft Internet Explorer 11의 수명 종료 후 클라이언트 콘솔에서 대시보드에 대한 HTML 렌더링 엔진이 Edge Chromium을 사용하여 Campaign Classic v7.3을 시작합니다.

이제 Microsoft Edge Webview 2 런타임의 설치 외에도 다음과 같습니다 [클라이언트 콘솔 설치에 필요합니다.](../../installation/using/installing-the-client-console.md#webview)이면 인스턴스에서 Microsoft Edge Chromium을 활성화해야 합니다.

## 영향을 받습니까?

환경이 Campaign Classic v7.3 이상으로 업그레이드된 경우 영향을 받습니다.

## 업데이트 방법

* 로서의 **호스팅** 고객, Adobe이 이미 인스턴스에서 Microsoft Edge Chromium을 활성화했습니다. 추가 작업은 필요하지 않습니다.

* 로서의 **온-프레미스/하이브리드** 고객 인스턴스에서 Microsoft Edge Chromium을 활성화해야 합니다.

   Campaign Classic v7.3 이상으로 업그레이드할 때 새로운 기능 `webView2Mode` 속성은 Campaign 서버 구성 파일에서 사용할 수 있습니다 `serverConf.xml`. 이 특성을 활성화해야 합니다.

   이렇게 하려면 모든 환경(MKT, MID, RT)에서 다음 단계를 적용합니다.

   1. Campaign 서버 구성 파일 편집(`serverConf.xml`)
   1. 에서 `<web>` 모듈, 설정 `webView2Mode = "1"`
   1. 다음 명령을 실행하여 서버 구성을 다시 로드합니다.

      ```
      nlserver config -reload
      ```

   1. 다음 명령을 실행하여 웹 서버를 다시 시작합니다.

      ```
      nlserver restart web
      ```

   1. 환경에서 Apache를 웹 서버로 사용하는 경우 다음 명령을 실행하여 Apache를 다시 시작합니다.

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>이러한 변경 사항에 대한 질문이 있으면 [Adobe 고객 지원 센터](https://helpx.adobe.com/kr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)에 문의하십시오.

## 관련 항목

* [환경 업그레이드](../../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [Campaign 클라이언트 콘솔 설치](../../installation/using/installing-the-client-console.md)
