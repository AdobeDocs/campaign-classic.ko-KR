---
product: campaign
title: Campaign 서버 구성
description: Campaign 서버 구성
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# Campaign 서버 구성 시작{#gs-campaign-server-config}



이 장에서는 요구 사항 및 환경 특성에 맞게 수행할 수 있는 서버측 구성에 대해 자세히 설명합니다.

## 제한 사항

이 절차는 다음으로 제한됩니다. **온-프레미스**/**잡종** 배포 및 관리 권한이 필요합니다.

대상 **호스트됨** 배포, 서버측 설정은 Adobe 전용으로만 구성할 수 있습니다. 그러나 일부 설정은 내에서 설정할 수 있습니다. [캠페인 Campaign 컨트롤 패널](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=ko)IP 허용 목록 관리 또는 URL 권한 등. [자세히 알아보기](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=ko)

자세한 내용은 다음 섹션을 참조하십시오.

* [컨트롤 패널 설명서](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=ko)
* [호스팅 모델](../../installation/using/hosting-models.md)
* [Campaign Classic 온-프레미스 및 호스팅 기능 매트릭스](../../installation/using/capability-matrix.md)

## 구성 파일

Campaign Classic 구성 파일은 **conf** Adobe Campaign 설치 폴더의 폴더입니다. 구성은 두 개의 파일에 분산됩니다.

* **serverConf.xml**: 모든 인스턴스에 대한 일반 구성 이 파일은 Adobe Campaign 서버의 기술 매개 변수를 결합합니다. 모든 인스턴스에서 공유합니다. 이러한 매개 변수 중 일부에 대한 설명은 아래에 자세히 설명되어 있습니다. 다른 노드 및 매개 변수 및 이에 나열되어 있음 [섹션](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (여기서 **인스턴스** 은 인스턴스의 이름입니다.): 인스턴스의 특정 구성입니다. 여러 인스턴스 간에 서버를 공유하는 경우 관련 파일에 각 인스턴스에 대한 매개 변수를 입력하십시오.

## 구성 범위

요구 사항과 구성에 따라 Campaign 서버를 구성하거나 조정합니다. 다음을 수행할 수 있습니다.

* 보안 설정 [내부 식별자](#internal-identifier)
* 사용 [캠페인 프로세스](#enabling-processes)
* 구성 [URL 권한](url-permissions.md)
* 정의 [보안 영역](security-zones.md)
* 구성 [Tomcat 설정](configure-tomcat.md)
* 사용자 지정 [게재 매개 변수](configure-delivery-settings.md)
* 정의 [다이내믹 페이지 보안 및 릴레이](#dynamic-page-security-and-relays)
* 목록 제한 [허용된 외부 명령](#restricting-authorized-external-commands)
* 설정 [중복 추적](#redundant-tracking)
* 관리 [고가용성 및 워크플로 친화성](#high-availability-workflows-and-affinities)
* 파일 관리 구성 - [자세히 알아보기](file-res-management.md)
   * 업로드 파일 형식 제한
   * 공개 리소스에 대한 액세스 활성화
   * 프록시 연결 구성
* [자동 프로세스 재시작](#automatic-process-restart)


## 내부 식별자 {#internal-identifier}

다음 **내부** 식별자는 설치, 관리 및 유지 관리를 위해 사용되는 기술 로그인입니다. 이 로그인은 인스턴스와 연결되어 있지 않습니다.

이 로그인을 사용하여 연결된 운영자는 모든 인스턴스에 대한 모든 권한을 갖게 됩니다. 새로 설치하는 경우 이 로그인에 암호가 없습니다. 이 암호를 수동으로 정의해야 합니다.

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

## 프로세스 활성화 {#enabling-processes}

서버의 Adobe Campaign 프로세스는 를 통해 활성화(및 비활성화)됩니다. **config-default.xml** 및 **`config-<instance>.xml`** 파일.

이러한 파일에 변경 사항을 적용하려면 Adobe Campaign 서비스가 시작된 경우 **nlserver 구성 -reload** 명령입니다.

프로세스에는 다중 인스턴스와 단일 인스턴스의 두 가지 유형이 있습니다.

* **다중 인스턴스**: 모든 인스턴스에 대해 하나의 단일 프로세스가 시작됩니다. 이 예는 다음과 같습니다. **웹**, **syslogd** 및 **trackinglogd** 프로세스.

   활성화는 다음에서 구성할 수 있습니다. **config-default.xml** 파일.

   클라이언트 콘솔에 액세스하고 리디렉션(추적)을 위해 Adobe Campaign 서버 선언:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   이 예제에서 파일은 **vi** linux의 명령. 다음을 사용하여 편집할 수 있습니다. **.txt** 또는 **.xml** 편집자.

* **모노 인스턴스**: 각 인스턴스에 대해 하나의 프로세스가 시작됩니다(모듈: **mta**, **wfserver**, **inMail**, **sms** 및 **통계**).

   인스턴스의 구성 파일을 사용하여 활성화를 구성할 수 있습니다.

   ```
   config-<instance>.xml
   ```

   게재를 위한 서버 선언, 워크플로우 인스턴스 실행 및 바운스 메일 복구:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Campaign 데이터 저장소**

스토리지 디렉터리(**var** 디렉토리): Adobe Campaign 데이터(로그, 다운로드, 리디렉션 등). 이렇게 하려면 **XTK_VAR_DIR** 시스템 변수:

* Windows에서는 **XTK_VAR_DIR** 시스템 변수

   ```
   D:\log\AdobeCampaign
   ```

* Linux에서 **customer.sh** 파일 및 표시: **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

   자세한 내용은 다음을 참조하십시오. [매개 변수 개인화](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## 다이내믹 페이지 보안 및 릴레이 {#dynamic-page-security-and-relays}

기본적으로 모든 동적 페이지는 **로컬** 웹 모듈이 시작된 시스템의 Tomcat 서버. 이 구성은 다음에 입력됩니다. **`<url>`** 섹션에 대한 쿼리 릴레이 구성의 섹션 **ServerConf.xml** 파일.

에서 동적 페이지의 실행을 릴레이할 수 있습니다. **원격** 서버(컴퓨터에서 웹 모듈이 활성화되지 않은 경우) 이렇게 하려면 다음을 교체해야 합니다. **localhost** jsp 및 JSSP용 원격 컴퓨터의 이름, 웹 응용 프로그램, 보고서 및 문자열

사용 가능한 다양한 매개 변수에 대한 자세한 내용은 **serverConf.xml** 구성 파일입니다.

JSP 페이지의 경우 기본 구성은 다음과 같습니다.

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign은 다음 JSP 페이지를 사용합니다.

* /nl/jsp/**soaprouter.jsp**: 클라이언트 콘솔 및 웹 서비스 연결(SOAP API),
* /nl/jsp/**m.jsp**: 미러 페이지,
* /nl/jsp/**logon.jsp**: 보고서 및 클라이언트 콘솔 배포에 대한 웹 기반 액세스,
* /nl/jsp/**s.jsp** : 바이럴 마케팅(후원 및 소셜 네트워크) 사용.

모바일 앱 채널에 사용되는 JSSP는 다음과 같습니다.

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**예제:**

클라이언트 시스템이 외부에서 연결되는 것을 방지할 수 있습니다. 이렇게 하려면 의 실행을 제한하면 됩니다. **soaprouter.jsp** 미러 페이지, 바이럴 링크, 웹 양식 및 공개 리소스의 실행만 승인합니다.

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

이 예에서는 **`<IP_addresses>`** 값은 이 마스크에 대한 릴레이 모듈을 사용하도록 승인된 IP 주소(쉼표로 구분) 목록과 일치합니다.

>[!NOTE]
>
>값은 구성 및 네트워크 제한에 따라 조정되며, 특히 설치에 맞게 특정 구성이 개발된 경우 더욱 그렇습니다.

### HTTP 헤더 관리 {#managing-http-headers}

기본적으로 모든 HTTP 헤더는 릴레이되지 않습니다. 릴레이로 보낸 응답에 특정 헤더를 추가할 수 있습니다. 방법은 다음과 같습니다.

1. 로 이동 **serverConf.xml** 파일.
1. 다음에서 **`<relay>`** 노드에서 릴레이된 HTTP 헤더 목록으로 이동합니다.
1. 추가 **`<responseheader>`** 다음 속성을 가진 요소:

   * **이름**: 헤더 이름
   * **값**: 값 이름입니다.

   예제:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 승인된 외부 명령 제한 {#restricting-authorized-external-commands}

빌드 8780에서 기술 관리자는 Adobe Campaign에서 사용할 수 있는 승인된 외부 명령 목록을 제한할 수 있습니다.

이렇게 하려면 사용을 금지할 명령 목록이 포함된 텍스트 파일을 만들어야 합니다. 예를 들면 다음과 같습니다.

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
>이 목록은 완전하지 않습니다.

다음에서 **exec** 서버 구성 파일의 노드에서는 이전에 만든 파일을 **blacklistFile** 특성.

**Linux에만 해당**: 서버 구성 파일에서 보안 구성을 향상시키기 위해 외부 명령 실행 전용 사용자를 지정하는 것이 좋습니다. 이 사용자는 **exec** 구성 파일의 노드입니다. 에서 사용할 수 있는 모든 매개 변수 **serverConf.xml** 다음에 나열됨 [섹션](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>사용자를 지정하지 않으면 모든 명령이 Adobe Campaign 인스턴스의 사용자 컨텍스트에서 실행됩니다. 사용자는 Adobe Campaign을 실행하는 사용자와 달라야 합니다.

예제:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

이 사용자는 &#39;neolane&#39; Adobe Campaign 연산자의 하위 사용자 목록에 추가되어야 합니다.

>[!IMPORTANT]
>
>사용자 지정 스도를 사용하면 안 됩니다. 표준 sudo를 시스템에 설치해야 합니다.


## 중복 추적 {#redundant-tracking}

리디렉션에 여러 서버를 사용하는 경우 리디렉션할 URL의 정보를 공유하려면 SOAP 호출을 통해 서로 통신할 수 있어야 합니다. 게재 시작 시 일부 리디렉션 서버를 사용하지 못할 수 있으므로 동일한 수준의 정보를 갖지 못할 수 있습니다.

>[!NOTE]
>
>표준 또는 엔터프라이즈 아키텍처를 사용하는 경우 주 애플리케이션 서버는 각 컴퓨터에서 추적 정보를 업로드할 수 있는 권한이 있어야 합니다.

중복 서버의 URL은 리디렉션 구성에서 다음을 통해 지정해야 합니다. **serverConf.xml** 파일.

**예제:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

다음 **enableIf** 속성은 선택 사항이며(기본적으로 비어 있음), 결과가 true인 경우에만 연결을 활성화할 수 있습니다. 이렇게 하면 모든 리디렉션 서버에서 동일한 구성을 얻을 수 있습니다.

컴퓨터의 호스트 이름을 얻으려면 다음 명령을 실행합니다. **호스트 이름 -s**.



## 고가용성 워크플로 및 관심도 {#high-availability-workflows-and-affinities}

여러 워크플로 서버(wfserver)를 구성하고 두 개 이상의 컴퓨터에 배포할 수 있습니다. 이 유형의 아키텍처를 선택하는 경우 Adobe Campaign 액세스에 따라 로드 밸런서의 연결 모드를 구성합니다.

웹에서 액세스하려면 다음을 선택합니다. **로드 밸런서** 연결 시간을 제한하는 모드입니다.

Adobe Campaign 콘솔을 통해 액세스하는 경우 다음을 선택합니다. **해시** 또는 **고정 ip** 모드. 이를 통해 리치 클라이언트와 서버 간의 연결을 유지할 수 있으며, 가져오기 또는 내보내기 작업 중에 사용자 세션이 중단되는 것을 방지할 수 있습니다.

특정 컴퓨터에서 워크플로우 또는 워크플로우 활동을 강제로 실행하도록 선택할 수 있습니다. 이렇게 하려면 관련 워크플로우 또는 활동에 대해 하나 이상의 관심도를 정의해야 합니다.

1. 워크플로우 또는 활동의 관심도를 **[!UICONTROL Affinity]** 필드.

   선호도 이름을 선택할 수 있지만 공백이나 구두점을 사용하지 않아야 합니다. 다른 서버를 사용하는 경우 다른 이름을 지정합니다.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   드롭다운 목록에는 이전에 사용한 관심도가 포함되어 있습니다. 입력한 값이 서로 다른 상태로 시간이 지남에 따라 완료됩니다.

1. 를 엽니다. **nl6/conf/config-`<instance>.xml`** 파일.
1. 일치하는 줄을 수정합니다. **[!UICONTROL wfserver]** 모듈은 다음과 같습니다.

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   여러 선호도를 정의하는 경우 공백 없이 쉼표로 구분해야 합니다.

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   관심도가 정의되지 않은 워크플로우를 실행하려면 관심도 이름 다음에 오는 쉼표가 필요합니다.

   관심도가 정의된 워크플로우만 실행하려면 관심도 목록의 끝에 쉼표를 추가하지 마십시오. 예를 들어 다음과 같이 선을 수정합니다.

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 자동 재시작 {#automatic-process-restart}

기본적으로 다른 Adobe Campaign 프로세스는 매일 오전 6시(서버 시간)에 자동으로 다시 시작됩니다.

그러나 이 구성은 변경할 수 있습니다.

이렇게 하려면 **serverConf.xml** 파일, 위치: **conf** 설치 저장소입니다.

이 파일에 구성된 각 프로세스에는 **processRestartTime** 특성. 이 속성 값을 수정하여 필요에 따라 각 프로세스의 재시작 시간을 조정할 수 있습니다.

>[!IMPORTANT]
>
>이 속성을 삭제하지 마십시오. 모든 프로세스는 매일 다시 시작해야 합니다.
