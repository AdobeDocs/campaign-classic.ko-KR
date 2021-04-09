---
solution: Campaign Classic
product: campaign
title: Campaign 서버 구성
description: Campaign 서버 구성
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 2%

---

# 캠페인 서버 구성 시작{#gs-campaign-server-config}

이 장에서는 요구 사항 및 환경 사양에 맞게 수행할 수 있는 서버측 구성에 대해 자세히 설명합니다.

## 제한 사항

이러한 절차는 **온-프레미스**/**하이브리드** 배포로 제한되며 관리 권한이 필요합니다.

**호스팅된** 배포의 경우 서버측 설정은 Adobe에서만 구성할 수 있습니다. 하지만 일부 설정은 [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html) 내에서 IP 허용 목록에 추가하다 관리나 URL 권한과 같이 설정할 수 있습니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)

자세한 내용은 다음 섹션을 참조하십시오.

* [Campaign 컨트롤 패널 설명서](https://docs.adobe.com/content/help/ko-KR/control-panel/using/control-panel-home.html)
* [호스팅 모델](../../installation/using/hosting-models.md)
* [Campaign Classic 온-프레미스 및 호스팅 기능 매트릭스](../../installation/using/capability-matrix.md)

## 구성 파일

Campaign Classic 구성 파일은 Adobe Campaign 설치 폴더의 **conf** 폴더에 저장됩니다. 구성은 2개의 파일에 분산됩니다.

* **serverConf.xml**:모든 인스턴스에 대한 일반 구성. 이 파일은 Adobe Campaign 서버의 기술 매개 변수를 결합합니다.모든 인스턴스에서 공유됩니다. 이러한 매개 변수 중 일부에 대한 설명은 아래에 자세히 나와 있습니다. 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열된 다른 노드 및 매개 변수입니다.
* **config-`<instance>`.xml** (여기서  **** instanceis the name of the instance):인스턴스의 특정 구성. 여러 인스턴스 간에 서버를 공유하는 경우 관련 파일의 각 인스턴스에 해당하는 매개 변수를 입력하십시오.

## 구성 범위

요구 사항 및 구성에 따라 Campaign 서버를 구성하거나 조정합니다. 다음을 수행할 수 있습니다.

* [내부 식별자 ](#internal-identifier)에 보안을 설정합니다.
* [캠페인 프로세스 사용](#enabling-processes)
* [URL 권한 ](url-permissions.md) 구성
* [보안 영역 정의](security-zones.md)
* [Tomcat 설정](configure-tomcat.md) 구성
* [배달 매개 변수 사용자 지정](configure-delivery-settings.md)
* [동적 페이지 보안 정의 및 relays](#dynamic-page-security-and-relays)
* [허용된 외부 명령 목록 제한](#restricting-authorized-external-commands)
* [중복 추적 설정](#redundant-tracking)
* [고가용성 및 워크플로우 친화성 관리](#high-availability-workflows-and-affinities)
* 파일 관리 구성 - [자세한 내용](file-res-management.md)
   * 업로드 파일 형식 제한
   * 공개 리소스에 대한 액세스 가능
   * 프록시 연결 구성
* [자동 프로세스 다시 시작](#automatic-process-restart)


## 내부 식별자 {#internal-identifier}

**internal** 식별자는 설치, 관리 및 유지 관리 목적으로 사용되는 기술 로그인입니다. 이 로그인은 인스턴스와 연결되어 있지 않습니다.

이 로그인을 사용하여 연결된 연산자는 모든 인스턴스에 대한 모든 권한을 갖습니다. 새 설치 시 이 로그인에는 암호가 없습니다. 이 암호를 수동으로 정의해야 합니다.

다음 명령을 사용하십시오.

```
nlserver config -internalpassword
```

그러면 다음 정보가 표시됩니다. 암호를 입력하고 확인합니다.

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## 프로세스 사용 {#enabling-processes}

서버의 Adobe Campaign 프로세스는 **config-default.xml** 및 **`config-<instance>.xml`** 파일을 통해 활성화(비활성화됨)됩니다.

이러한 파일에 변경 내용을 적용하려면 Adobe Campaign 서비스가 시작된 경우 **nlserver config -reload** 명령을 실행해야 합니다.

두 가지 유형의 프로세스가 있습니다.다중 인스턴스 및 단일 인스턴스.

* **다중 인스턴스**:하나의 단일 프로세스가 모든 인스턴스에 대해 시작됩니다. 이것은 **web**, **syslogd** 및 **trackinglogd** 프로세스에 대한 경우입니다.

   지원은 **config-default.xml** 파일에서 구성할 수 있습니다.

   클라이언트 콘솔에 액세스하고 리디렉션(추적)을 위해 Adobe Campaign 서버를 선언합니다.

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   이 예에서 파일은 Linux에서 **vi** 명령을 사용하여 편집됩니다. **.txt** 또는 **.xml** 편집기를 사용하여 편집할 수 있습니다.

* **모노 인스턴스**:각 인스턴스에 대해 하나의 프로세스가 시작됩니다(모듈: **mta** wfserver **,** inMail **,** smsand  ****   **** stat).

   인스턴스의 구성 파일을 사용하여 지원을 구성할 수 있습니다.

   ```
   config-<instance>.xml
   ```

   배달 서버 선언, 워크플로 인스턴스 실행 및 바운스 메일 복구:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**캠페인 데이터 스토리지**

Adobe Campaign 데이터의 저장소 디렉토리(**var** 디렉토리)를 구성할 수 있습니다(로그, 다운로드, 리디렉션 등). 이렇게 하려면 **XTK_VAR_DIR** 시스템 변수를 사용합니다.

* Windows의 경우 **XTK_VAR_DIR** 시스템 변수에 다음 값을 지정합니다.

   ```
   D:\log\AdobeCampaign
   ```

* Linux에서 **customer.sh** 파일로 이동하여 다음을 표시합니다.**XTK_VAR_DIR=/app/log/AdobeCampaign** 내보내기

   자세한 내용은 [매개 변수 개인화](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)를 참조하십시오.


## 동적 페이지 보안 및 다시 표시 {#dynamic-page-security-and-relays}

기본적으로 모든 동적 페이지는 웹 모듈이 시작된 컴퓨터의 **local** Tomcat 서버와 자동으로 연결됩니다. 이 구성은 **ServerConf.xml** 파일의 쿼리 릴레이 구성의 **`<url>`** 섹션에 입력됩니다.

**원격** 서버에서 동적 페이지의 실행을 릴레이 수 있습니다.컴퓨터에서 웹 모듈이 활성화되지 않은 경우 이렇게 하려면 **localhost**&#x200B;를 JSP 및 JSSP, 웹 애플리케이션, 보고서 및 문자열에 대한 원격 컴퓨터의 이름으로 바꾸어야 합니다.

사용 가능한 다양한 매개 변수에 대한 자세한 내용은 **serverConf.xml** 구성 파일을 참조하십시오.

JSP 페이지의 기본 구성은 다음과 같습니다.

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign은 다음 JSP 페이지를 사용합니다.

* /nl/jsp/**soaprouter.jsp**:클라이언트 콘솔 및 웹 서비스 연결(SOAP API),
* /nl/jsp/**m.jsp**:페이지,
* /nl/jsp/**logon.jsp**:보고서에 대한 웹 기반 액세스 및 클라이언트 콘솔 배포,
* /nl/jsp/**s.jsp** :바이러스 마케팅(후원 및 소셜 네트워크) 사용

모바일 앱 채널에 사용되는 JSSP는 다음과 같습니다.

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**예제:**

클라이언트 컴퓨터가 외부에서 연결되지 않도록 할 수 있습니다. 이렇게 하려면 **soprouter.jsp**&#x200B;의 실행을 제한하고 미러 페이지, 바이럴 링크, 웹 양식 및 공개 리소스의 실행만 승인합니다.

매개 변수는 다음과 같습니다.

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

이 예제에서 **`<IP_addresses>`** 값은 이 마스크에 릴레이 모듈을 사용할 수 있는 IP 주소(쉼표로 구분) 목록과 일치합니다.

>[!NOTE]
>
>특히 특정 구성이 설치용으로 개발된 경우, 구성 및 네트워크 제한에 따라 값이 조정됩니다.

### HTTP 헤더 관리 {#managing-http-headers}

기본적으로 모든 HTTP 헤더는 전달되지 않습니다. 릴레이로 보낸 답글에 특정 헤더를 추가할 수 있습니다. 방법은 다음과 같습니다.

1. **serverConf.xml** 파일로 이동합니다.
1. **`<relay>`** 노드에서 릴레이된 HTTP 헤더 목록으로 이동합니다.
1. 다음 특성을 사용하여 **`<responseheader>`** 요소를 추가합니다.

   * **이름**:헤더 이름
   * **값**:값 이름.

   예제:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 허가된 외부 명령 {#restricting-authorized-external-commands} 제한

기술 관리자는 빌드 8780에서 Adobe Campaign에서 사용할 수 있는 인증된 외부 명령 목록을 제한할 수 있습니다.

이렇게 하려면 다음과 같이 사용할 수 없게 하려는 명령 목록이 포함된 텍스트 파일을 만들어야 합니다.

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>이 목록은 완전하지 않다.

서버 구성 파일의 **exec** 노드에서 이전에 만든 파일을 **blacklistFile** 특성에서 참조해야 합니다.

**Linux 전용**:서버 구성 파일에서 보안 구성을 강화하기 위해 외부 명령 실행에 전용 사용자를 지정하는 명령을 다시 수행합니다. 이 사용자는 구성 파일의 **exec** 노드에서 설정됩니다. **serverConf.xml**&#x200B;에 사용 가능한 모든 매개 변수가 이 [섹션](../../installation/using/the-server-configuration-file.md)에 나열됩니다.

>[!NOTE]
>
>사용자를 지정하지 않으면 Adobe Campaign 인스턴스의 사용자 컨텍스트에서 모든 명령이 실행됩니다. 사용자는 Adobe Campaign을 실행하는 사용자와 달라야 합니다.

예제:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

이 사용자를 &#39;Neolane&#39; Adobe Campaign 연산자의 사용자 목록에 추가해야 합니다.

>[!IMPORTANT]
>
>사용자 정의 sudo를 사용하면 안 됩니다. 표준 사용자를 시스템에 설치해야 합니다.


## 중복된 추적 {#redundant-tracking}

리디렉션에 여러 서버를 사용하는 경우 리디렉션할 URL에서 정보를 공유하려면 SOAP 호출을 통해 서로 통신할 수 있어야 합니다. 배달 시작 시 일부 리디렉션 서버를 사용할 수 없을 수 있습니다.따라서 같은 수준의 정보를 가지고 있지 않을 수도 있습니다.

>[!NOTE]
>
>표준 또는 엔터프라이즈 아키텍처를 사용할 때는 각 컴퓨터에서 추적 정보를 업로드할 수 있는 기본 응용 프로그램 서버가 인증되어야 합니다.

중복 서버의 URL은 리디렉션 구성에서 **serverConf.xml** 파일을 통해 지정해야 합니다.

**예제:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf** 속성은 선택 사항이며(기본적으로 비어 있음) 결과가 true인 경우에만 연결을 활성화할 수 있습니다. 이렇게 하면 모든 리디렉션 서버에서 동일한 구성을 얻을 수 있습니다.

컴퓨터의 호스트 이름을 얻으려면 다음 명령을 실행하십시오.**hostname -s**.



## 고가용성 워크플로우 및 친화성 {#high-availability-workflows-and-affinities}

여러 워크플로 서버(wfserver)를 구성하고 두 대 이상의 컴퓨터에 배포할 수 있습니다. 이 유형의 아키텍처를 선택하는 경우 Adobe Campaign 액세스에 따라 부하 분산 장치의 연결 모드를 구성합니다.

웹에서 액세스하려면 **부하 균형 조정기** 모드를 선택하여 연결 시간을 제한합니다.

Adobe Campaign 콘솔을 통해 액세스하는 경우 **해시** 또는 **고정 ip** 모드를 선택합니다. 이렇게 하면 리치 클라이언트와 서버 간의 연결을 유지할 수 있으며 가져오기 또는 내보내기 작업 중 사용자 세션이 중단되는 것을 방지할 수 있습니다.

특정 컴퓨터에서 워크플로우 또는 워크플로우 활동을 강제로 실행하도록 선택할 수 있습니다. 이를 수행하려면 관련 워크플로우 또는 활동에 대해 하나 이상의 친화성을 정의해야 합니다.

1. **[!UICONTROL Affinity]** 필드에 워크플로우 또는 활동의 친화성을 입력합니다.

   친화성 이름을 선택할 수 있지만 공백이나 구두점 표시를 사용하지 않아야 합니다. 다른 서버를 사용하는 경우 다른 이름을 지정합니다.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   드롭다운 목록에는 이전에 사용한 친화성이 포함되어 있습니다. 입력한 값이 다른 시간에 따라 완료됩니다.

1. **nl6/conf/config-`<instance>.xml`** 파일을 엽니다.
1. 다음과 같이 **[!UICONTROL wfserver]** 모듈과 일치하는 행을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   여러 친화성을 정의하는 경우 공백 없이 쉼표로 구분해야 합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   친화성이 정의되지 않은 워크플로우를 실행하려면 친화성 이름 뒤에 오는 쉼표가 필요합니다.

   선호도가 정의된 워크플로우만 실행하려면 친화성 목록의 끝에 쉼표를 추가하지 마십시오. 예를 들어 다음과 같이 라인을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## {#automatic-process-restart} 자동 다시 시작

기본적으로 서로 다른 Adobe Campaign 프로세스는 매일 오전 6시(서버 시간)에 자동으로 다시 시작됩니다.

하지만 이 구성을 변경할 수 있습니다.

이렇게 하려면 설치의 **conf** 저장소에 있는 **serverConf.xml** 파일로 이동합니다.

이 파일에 구성된 각 프로세스에는 **processRestartTime** 특성이 있습니다. 이 속성의 값을 수정하여 각 프로세스의 재시작 시간을 필요에 따라 조정할 수 있습니다.

>[!IMPORTANT]
>
>이 특성을 삭제하지 마십시오. 모든 프로세스는 매일 다시 시작해야 합니다.
