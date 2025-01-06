---
product: campaign
title: Windows용 웹 서버에 통합
description: Windows용 웹 서버에 통합
feature: Installation, Instance Settings
badge-v7-prem: label="온-프레미스/하이브리드만" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=ko" tooltip="온-프레미스 및 하이브리드 배포에만 적용"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 2%

---

# Windows용 웹 서버에 통합 {#integration-into-a-web-server-for-windows}

Adobe Campaign에는 HTTP(및 SOAP)를 통해 애플리케이션 서버에서 진입점 역할을 하는 Apache Tomcat이 포함되어 있습니다.

통합된 이 Tomcat 서버를 사용하여 HTTP 요청을 처리할 수 있습니다.

이 경우:

* 기본 수신 포트는 8080입니다. 변경하려면 [이 섹션](../../installation/using/configure-tomcat.md)을 참조하세요.
* 그런 다음 클라이언트 콘솔은 ```https:// `<computer>`:8080```과(와) 같은 URL을 사용하여 연결합니다.

그러나 보안 및 관리상의 이유로 Adobe Campaign을 실행 중인 컴퓨터가 인터넷에 노출되어 네트워크 외부의 콘솔에 대한 액세스를 열고자 할 때 HTTP 트래픽의 기본 진입점으로 전용 웹 서버를 사용하는 것이 좋습니다.

웹 서버를 사용하면 HTTPs 프로토콜로 데이터 기밀성을 보장할 수도 있습니다.

마찬가지로 추적 기능을 사용하려면 웹 서버를 사용해야 합니다. 이 기능은 웹 서버 확장 모듈로만 사용할 수 있습니다.

## IIS 웹 서버 구성 {#configuring-the-iis-web-server}

Microsoft IIS 웹 서버의 구성 절차는 대부분 그래픽입니다. 웹 사이트를 사용하여 Java(.jsp) 파일, 스타일시트(.css, .xsl), 이미지(.png), 리디렉션용 ISAPI DLL 등 Adobe Campaign 서버의 리소스에 액세스합니다.


### 구성 단계 {#configuration-steps}

Adobe Campaign을 Microsoft IIS 웹 서버와 통합하려면 다음 단계를 수행합니다.

1. Microsoft IIS를 엽니다.
1. 네트워크의 매개 변수(TCP 연결 포트, DNS 호스트, IP 주소)에 따라 사이트(예: Adobe Campaign)를 만들고 구성합니다.

   최소한 사이트의 이름과 가상 디렉터리에 대한 액세스 경로를 지정해야 합니다. 웹 사이트 디렉터리에 액세스하는 경로는 사용되지 않으므로 다음 디렉터리를 사용할 수 있습니다.

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. **VBS** 스크립트를 사용하면 방금 만든 가상 디렉터리에서 Adobe Campaign 서버에서 사용하는 리소스를 자동으로 구성할 수 있습니다. 시작하려면 `[INSTALL]\conf` 폴더에 있는 **iis_neolane_setup.vbs** 파일을 두 번 클릭합니다. 여기서 `[INSTALL]`은(는) Adobe Campaign 설치 폴더에 액세스하는 경로입니다.

   >[!NOTE]
   >
   >VBS 스크립트를 실행하거나 관리자로 스크립트를 실행하려면 관리자로 로그인해야 합니다.

   웹 서버가 추적 리디렉션 서버로 사용되는 경우 **[!UICONTROL OK]**&#x200B;을(를) 클릭하고, 그렇지 않으면 **[!UICONTROL Cancel]**&#x200B;을(를) 클릭합니다.

   웹 서버에 여러 사이트가 이미 구성된 경우 설치할 웹 사이트를 지정할 중간 페이지가 표시됩니다. 사이트에 연결된 번호를 입력하고 **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다.

1. **[!UICONTROL Content View]** 탭에서 웹 사이트가 Adobe Campaign 리소스로 올바르게 구성되었는지 확인합니다.

   트리가 표시되지 않으면 Microsoft IIS를 다시 시작합니다.

### 권한 관리 {#managing-rights}

그런 다음 ISAPI DLL 및 Adobe Campaign 설치 디렉터리의 리소스에 대한 보안 설정을 구성해야 합니다.

그렇게 하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Features View]** 탭을 선택하고 **인증** 링크를 두 번 클릭합니다.

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. 웹 사이트의 **디렉터리 보안** 탭에서 익명 액세스가 활성화되어 있는지 확인하십시오. 필요한 경우 **[!UICONTROL Edit]** 링크를 클릭하여 설정을 변경합니다.

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### 웹 서버 실행 및 구성 테스트 {#launching-the-web-server-and-testing-the-configuration}

이제 구성이 올바른지 테스트해야 합니다.

이렇게 하려면 다음 절차를 적용합니다.

1. **iisreset** 명령줄을 사용하여 Microsoft IIS 서버를 다시 시작하십시오.

1. Adobe Campaign 서비스를 시작한 다음 실행 중인지 확인합니다.

1. 웹 브라우저에 다음 URL을 삽입하여 추적 모듈을 테스트합니다.

   ```
   https://<computer>/r/test
   ```

   브라우저에 다음 응답이 표시됩니다.

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

리디렉션 모듈이 있는지 테스트하려면 다음 명령줄을 실행합니다.

```
nlserver pdump
```

다음 정보를 반환해야 합니다.

```sql
HH:MM:SS >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

ISAPI DLL이 올바르게 로드되었는지 확인할 수도 있습니다.

그렇게 하려면 다음 단계를 적용합니다.

1. **[!UICONTROL Driver mapping]** 아이콘을 클릭하여 Adobe Campaign 사이트에 대한 ISAPI 필터를 편집합니다.
1. ISAPI 필터의 콘텐츠를 확인합니다.


## 업로드 파일 크기 제한 변경 {#changing-the-upload-file-size-limit}

IIS 웹 서버를 구성할 때 서버에 업로드되는 집합 파일에 대해 약 28MB의 제한이 자동으로 적용됩니다.

특히 이 제한보다 큰 파일을 업로드하려는 경우 Adobe Campaign에 영향을 줄 수 있습니다.

예를 들어 워크플로우에서 **데이터 로드(파일)** 유형 활동을 사용하여 50MB 파일을 가져오는 경우 오류가 발생하면 워크플로우가 올바르게 실행되지 않습니다.

이 경우 이 제한을 늘려야 합니다.

이 Microsoft IIS 옵션에 대한 자세한 내용은 [Microsoft 설명서](https://learn.microsoft.com/en-us/iis/configuration/system.webServer/security/requestFiltering/requestLimits/){target="_blank"}의 &quot;HowTo&quot; 섹션을 참조하십시오.

