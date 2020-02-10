---
title: 업그레이드
seo-title: 업그레이드
description: 업그레이드
seo-description: null
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 업그레이드{#upgrading}

업그레이드 프로세스를 시작하기 전에 업그레이드할 Adobe Campaign 버전을 확인하고 릴리스 정보를 [참조하십시오](https://docs.campaign.adobe.com/doc/AC/en/RN.html).

>[!CAUTION]
>
>업데이트하기 전에 각 인스턴스에서 데이터베이스를 백업하는 것이 좋습니다. 자세한 내용은 백업을 [참조하십시오](../../production/using/backup.md).\
>업그레이드를 수행하려면 인스턴스 및 로그에 액세스할 수 있는 기능과 권한이 있어야 합니다.

>[!NOTE]
>
>또한 [설치 가이드](../../installation/using/general-architecture.md) 및 [빌드 업그레이드를](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 시작합니다.

## Windows {#in-windows}

새 빌드를 제공할 때 새 버전으로 Adobe Campaign을 업데이트하려면 Windows에서 다음 절차를 적용해야 합니다.

* [서비스](#shut-down-services)종료,
* [Adobe Campaign 서버 애플리케이션](#upgrade-the-adobe-campaign-server-application)업그레이드,
* [리소스](#synchronize-resources)동기화,
* [서비스를](#restart-services)다시 시작합니다.

클라이언트 콘솔을 업데이트하는 방법에 대해 알아보려면 [이 섹션을](../../installation/using/client-console-availability-for-windows.md)참조하십시오.

### 서비스 종료 {#shut-down-services}

모든 파일을 새 버전으로 바꾸려면 nlserver 서비스의 모든 인스턴스를 종료해야 합니다.

1. 다음 서비스를 종료합니다.

   * 웹 서비스(IIS):

      **iisreset /stop**

   * Adobe Campaign 서비스: **net stop nlserver6**
   >[!CAUTION]
   >
   >또한 리디렉션 서버(webmdl)를 중지하여 IIS에서 사용하는 **nlsrvmod.dll** 파일을 새 버전으로 바꿀 수 있도록 해야 합니다.

1. nlserver pdump 명령을 실행하여 활성화된 작업이 **없는지** 확인합니다. 다음과 같은 사항이 해당됩니다.

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Windows 작업 관리자를 사용하여 모든 프로세스가 중지되었는지 확인할 수 있습니다.

### Adobe Campaign 서버 애플리케이션 업그레이드 {#upgrade-the-adobe-campaign-server-application}

업그레이드 파일을 실행하려면 다음 단계를 수행하십시오.

1. setup.exe를 **실행합니다**.

   이 파일을 다운로드하려면 다운로드 센터 링크를 통해 Adobe Campaign 지원 페이지( [https://support.neolane.net/](https://support.neolane.net/)) **로** 이동합니다.

1. 설치 모드를 선택합니다.선택 **[!UICONTROL Update or repair]**
1. 클릭 **[!UICONTROL Next]** .
1. 클릭 **[!UICONTROL Finish]** .

   그런 다음 설치 프로그램이 새 파일을 복사합니다.

1. 작업이 완료되면 을 클릭합니다 **[!UICONTROL Finish]** .

### 리소스 동기화 {#synchronize-resources}

다음 명령줄을 사용합니다.

**nlserver config -postupgrade -allinstances**

이렇게 하면 다음 작업을 수행할 수 있습니다.

* 리소스 동기화,
* 스키마 업데이트,
* 데이터베이스를 업데이트합니다.

>[!NOTE]
>
>이 작업은 한 번만 수행되어야 하며 (**nlserver web**) 응용 프로그램 서버에서만 수행해야 합니다.

그런 다음 동기화가 오류를 생성했는지 또는 경고를 생성했는지 확인합니다. 자세한 내용은 업그레이드 충돌 [해결을 참조하십시오](#resolving-upgrade-conflicts).

### 서비스 다시 시작 {#restart-services}

다시 시작할 서비스는 다음과 같습니다.

* 웹 서비스(IIS):

   **iisreset /start**

* Adobe Campaign 서비스: **net start nlserver6**

## Linux {#in-linux}

새 빌드가 제공될 때 새 버전으로 Adobe Campaign을 업데이트하려면 Linux에 대한 절차는 다음과 같습니다.

* [업데이트된 패키지](#obtain-updated-packages),
* [업데이트](#perform-an-update)수행,
* [웹 서버를](#reboot-the-web-server)다시 부팅합니다.

클라이언트 콘솔을 업데이트하는 방법에 대해 알아보려면 [이 섹션을](../../installation/using/client-console-availability-for-linux.md)참조하십시오.

>[!NOTE]
>
>빌드 8757에서 타사 라이브러리는 더 이상 필요하지 않습니다.

### 업데이트된 패키지 가져오기 {#obtain-updated-packages}

Adobe Campaign의 업데이트된 패키지 모두 복구하여 시작합니다.다운로드 센터 링크를 통해 Adobe Campaign 지원 페이지( [https://support.neolane.net/](https://support.neolane.net/)) **로** 이동합니다.

파일은 **nlserver6-v7-XXX.rpm입니다.**

### 업데이트 수행 {#perform-an-update}

* RPM 기반 배포(RedHat, SuSe)

   설치하려면 루트로 실행합니다.

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   여기서 XXX는 파일의 버전입니다.

   rpm 파일에는 CentOS/Red Hat 배포에서 찾을 수 있는 패키지에 대한 종속성이 있습니다. 이러한 종속성 중 일부를 사용하지 않으려면 rpm의 &quot;nodeps&quot; 옵션을 사용해야 할 수 있습니다.

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* DEB 기반 배포(Debian)

   설치하려면 루트로 실행합니다.

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>전체 설치 절차는 [이 섹션에](../../installation/using/installing-campaign-standard-packages.md)자세히 설명되어 있습니다. 리소스는 자동으로 동기화되지만 오류가 발생하지 않도록 해야 합니다. 자세한 내용은 업그레이드 충돌 [해결을 참조하십시오](#resolving-upgrade-conflicts).

### 웹 서버 재부팅 {#reboot-the-web-server}

새 라이브러리를 적용하려면 Apache를 종료해야 합니다.

이렇게 하려면 다음 명령을 실행합니다.

```
/etc/init.d/apache stop
```

>[!CAUTION]
>
>* 스크립트를 **apache** 대신 **httpd라고 할 수 있습니다**.
>* 다음 응답을 받을 때까지 이 명령을 실행해야 합니다.
   >Apache가 새 라이브러리를 적용하려면 이 작업이 필요합니다.
>



그런 다음 Apache를 다시 시작합니다.

```
/etc/init.d/apache start
```

## 업그레이드 충돌 해결 {#resolving-upgrade-conflicts}

리소스를 동기화하는 동안 **업그레이드** 후 명령을 사용하여 동기화가 오류를 생성했는지 또는 경고를 생성했는지 여부를 감지할 수 있습니다.

### 동기화 결과 보기 {#view-the-synchronization-result}

다음 두 가지 방법으로 동기화 결과를 볼 수 있습니다.

* 명령줄 인터페이스에서 3단계 V형 **>>>** V자식으로 오류가 발생하고 동기화가 자동으로 중지됩니다. 경고는 이중 V형 **>>** 에 의해 구현되며 동기화가 완료되면 해결되어야 합니다. 업그레이드 후 종료 시 명령 프롬프트에 요약이 표시됩니다. 다음과 같이 표시됩니다.

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   경고가 리소스의 충돌을 우려하면 문제를 해결하기 위해 사용자의 주의가 필요합니다.

* postupgrade_ **.log`<server version number>_<time of postupgrade>`** 로그 파일에는 동기화 결과가 들어 있습니다. 다음 디렉토리에서 기본적으로 사용할 수 있습니다. **`<installation directory>/var/<instance/postupgrade`** Adobe 오류 및 경고는 오류 및 경고 속성으로 표시됩니다.

### 충돌 해결 {#resolving-conflicts}

충돌을 해결하려면 다음 프로세스를 적용합니다.

1. Adobe Campaign 트리에서 로 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 이동합니다.
1. 목록에서 해결할 충돌을 선택합니다.

다음 세 가지 방법으로 충돌을 해결할 수 있습니다.

* **[!UICONTROL Declare as resolved]** :사전 사용자 개입이 필요합니다.
* **[!UICONTROL Accept the new version]** :사용자가 Adobe Campaign과 함께 제공된 리소스를 변경하지 않은 경우 권장합니다.
* **[!UICONTROL Keep the current version]** :은 업데이트가 거부됨을 의미합니다.

   >[!CAUTION]
   >
   >이 해상도 모드를 선택하면 새 버전의 수정 기능을 사용할 수 없습니다.

충돌을 수동으로 해결하도록 선택한 경우 다음과 같이 진행하십시오.

1. 창의 아래쪽 섹션에서 **_충돌_** 문자열을 검색하여 충돌하는 엔티티를 찾습니다. 새 버전과 함께 설치되는 엔티티에는 **new** 인수가 포함되어 있으며, 이전 버전과 일치하는 엔티티에는 **cus** 인수가 포함되어 있습니다.

   ![](assets/s_ncs_production_conflict002.png)

1. 보관하지 않을 버전을 삭제합니다. 유지하는 엔티티의 **_conflict_argument_** 문자열을 삭제합니다.

   ![](assets/s_ncs_production_conflict003.png)

1. 해결된 충돌로 이동합니다. 아이콘을 **[!UICONTROL Actions]** 클릭하고 **[!UICONTROL Declare as resolved]** 을 선택합니다.
1. 변경 내용 저장:이제 충돌이 해결되었습니다.

### 모범 사례 {#best-practices}

업데이트 오류가 데이터베이스 구성에 연결되어 있을 수 있습니다. 기술 관리자와 데이터베이스 관리자가 수행한 구성이 호환되는지 확인하십시오.

예를 들어, 유니코드 데이터베이스는 LATIN1 데이터 등의 저장영역만 승인하지 않아야 합니다.

## 사용 가능한 업데이트에 대한 클라이언트 콘솔 경고 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

(nlserver web ****) Adobe Campaign 응용 프로그램 서버가 설치된 컴퓨터에서 파일을 다운로드하고 복사합니다

**setup-client-6.** XXXX **.exe**

in **[path of application]**datakintenzjsp

다음 번에 클라이언트 콘솔이 연결되면 사용자에게 업데이트 사용 가능 여부를 알리고 다운로드 및 설치 가능성을 제공합니다.

>[!NOTE]
>
>IIS_XPG 사용자에게 이 설치 파일에 대한 적절한 읽기 권한이 있는지 확인하고 자세한 내용은 [설치 가이드를](../../installation/using/general-architecture.md) 참조하십시오.

### Linux {#in-linux-1}

Adobe Campaign 응용 프로그램 서버(**nlserver 웹**)가 설치된 컴퓨터에서 다음 패키지를 검색합니다.

**setup-client-6.** XXXX **.exe**

를 복사하여 /usr/local/neolane/nl6/datakit/nl/eng/jsp로 ****&#x200B;저장:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

다음 번에 클라이언트 콘솔이 연결되면 사용자에게 업데이트 사용 가능 여부를 알리고 다운로드 및 설치 가능성을 제공합니다.

>[!NOTE]
>
>Apache 사용자에게 이 설치 파일에 대한 적절한 읽기 권한이 있는지 확인하고 자세한 내용은 [설치 가이드를](../../installation/using/general-architecture.md) 참조하십시오.

