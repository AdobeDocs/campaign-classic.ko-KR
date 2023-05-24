---
product: campaign
title: 기술 정보 - Campaign 환경에서 Microsoft Edge Chromium 활성화
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
description: Campaign - 에지 크롬
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---

# 환경에서 Microsoft Edge Chromium을 활성화하는 방법 {#edge-conf}




## 변경 사항

Microsoft Internet Explorer 11의 수명 종료에 따라 클라이언트 콘솔의 대시보드용 HTML 렌더링 엔진은 Edge Chromium을 사용하여 Campaign Classic v7.3을 시작합니다.

Microsoft Edge Webview 2 런타임 설치, 이제 [클라이언트 콘솔 설치에 필요](../../installation/using/installing-the-client-console.md#webview), 인스턴스에서 Microsoft Edge Chromium을 활성화해야 합니다.

## 영향을 받습니까?

환경이 Campaign Classic v7.3 이상으로 업그레이드된 경우 영향을 받습니다.

## 업데이트 방법

* 로서의 **호스트됨** 고객 Adobe이 인스턴스에서 Microsoft Edge Chromium을 이미 활성화했습니다. 추가 작업은 필요하지 않습니다.

* (으)로 **온-프레미스/하이브리드** 고객은 인스턴스에서 Microsoft Edge Chromium을 활성화해야 합니다.

   Campaign Classic v7.3 이상으로 업그레이드할 때 `webView2Mode` 속성은 캠페인 서버 구성 파일에서 사용할 수 있습니다 `serverConf.xml`. 이 특성을 활성화해야 합니다.

   이렇게 하려면 모든 환경(MKT, MID, RT)에 다음 단계를 적용합니다.

   1. Campaign 서버 구성 파일(`serverConf.xml`)
   1. 다음에서 `<web>` 모듈, 설정 `webView2Mode = "1"`
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

## 관련 항목

* [환경 업그레이드](../../production/using/build-upgrade.md)
* [빌드 업그레이드 FAQ](../../platform/using/faq-build-upgrade.md)
* [Campaign 클라이언트 콘솔 설치](../../installation/using/installing-the-client-console.md)
