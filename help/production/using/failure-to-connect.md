---
title: 연결 실패
seo-title: 연결 실패
description: 연결 실패
seo-description: null
page-status-flag: never-activated
uuid: 5e4cf47d-9699-4b4c-9c45-064fdc17110a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 493067fb-68f1-48b9-afaa-3127a847db83
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 90813bc2913d56136067b9f64c0e934df3f17473

---


# 연결 실패{#failure-to-connect}

이유는 여러 개이며 다양한 컨텍스트에 따라 다릅니다.

보안 영역의 일반 구성을 확인합니다.

>[!NOTE]
>
>보안 영역 구성에 대한 자세한 내용은 [이 섹션을](../../installation/using/configuring-campaign-server.md#defining-security-zones)참조하십시오.

다음 정보를 확인하십시오.

1. **네트워크 검사**

   * 당신 컴퓨터에서 인터넷 연결이 되나요?

      인터넷(예:)에서 웹 사이트에 연결할 수 있는지 확인합니다. 연결할 수 없는 경우 컴퓨터에 문제가 있습니다. 시스템 관리자에게 문의하십시오.

   * 다른 서비스를 통해 Adobe Campaign을 호스팅하는 서버에 연결할 수 있습니까?

      SSH 또는 다른 수단을 통해 서버에 연결합니다. 가능하지 않으면 호스팅 회사에 문제가 발생합니다. 시스템 관리자에게 문의하십시오.

1. **웹 서버측** (IIS/apache 등)에서 확인

   * 웹 서버가 응답합니까?

      웹 브라우저를 사용하여 Adobe Campaign 서버 액세스 URL에 연결: **http(s)://`<urlserver>`**를 참조하십시오. 응답하지 않으면 웹 서버가 컴퓨터에서 중지됩니다. 서비스를 다시 시작하려면 호스트 회사의 시스템 관리자에게 문의하십시오.

   * Adobe Campaign이 제대로 통합되었습니까?

      다음에 로그온합니다. **http(s)://`<urlserver>`/r/test** URL. 서버는 다음 유형의 메시지를 반환해야 합니다.

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      이 결과를 얻지 못한 경우 통합을 고려하도록 웹 서버 구성을 확인하십시오.

1. **Adobe Campaign 쪽에서 확인**

   * Adobe Campaign 웹 모듈이 실행되었습니까?

      다음 URL에 연결: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Tomcat Java 오류가 발생하는 경우:

         JAVA 통합이 올바르게 수행됩니까? Adobe Campaign을 사용하려면 SUN JDK가 필요합니다.

         이 파일은 /nl6/customer.sh 파일에 **`[path of application]`통합되었습니다.**

      * 빈 페이지를 얻는 경우:

         Adobe Campaign 웹 모듈이 시작되었습니까? 다음 사항을 얻어야 합니다.

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * 그렇지 않은 경우 다음 명령을 사용하여 다시 시작합니다.

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Adobe Campaign 모듈을 나열할 때 다음 유형의 응답을 얻는 경우: **nlserver pdump**
>HH:MM:SS > Adobe Campaign Classic(7.X YY.R 빌드 XXX@SHA1)용 응용 프로그램 서버 DD/MM/YYYY 작업 없음 전체 Adobe Campaign 응용 프로그램을 다시 시작해야 합니다. 이렇게 하려면 다음 명령을 사용합니다.**nlserver watchdog -svc -noconsole **
