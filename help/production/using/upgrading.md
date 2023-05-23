---
product: campaign
title: 새 빌드로 업그레이드
description: 새 빌드로 업그레이드하는 기술 단계 알아보기
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 3%

---

# 새 빌드로 업그레이드 중(온-프레미스){#upgrading}



업그레이드 프로세스를 시작하기 전에 업그레이드할 Adobe Campaign 버전을 확인하고 다음을 참조하십시오. [릴리스 정보](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe은 업데이트하기 전에 각 인스턴스에서 데이터베이스 백업을 수행할 것을 강력히 권장합니다. 자세한 정보는 [이 섹션](../../production/using/backup.md)을 참조하십시오.
>* 업그레이드를 수행하려면 인스턴스 및 로그에 액세스할 수 있는 권한과 권한이 있는지 확인하십시오.
>* 읽기 [이 섹션](../../installation/using/general-architecture.md) 및 [빌드 업그레이드](https://helpx.adobe.com/kr/campaign/kb/acc-build-upgrade.html) 시작 전 챕터.
>


## Windows {#in-windows}

Windows 환경에서 아래 단계에 따라 Adobe Campaign을 새 빌드로 업데이트합니다.

* [서비스 종료](#shut-down-services),
* [애플리케이션 서버 업그레이드](#upgrade-the-adobe-campaign-server-application),
* [리소스 동기화](#synchronize-resources),
* [서비스 다시 시작](#restart-services).

클라이언트 콘솔을 업데이트하는 방법에 대해 알아보려면 다음을 참조하십시오. [이 섹션](../../installation/using/client-console-availability-for-windows.md).

### 서비스 종료 {#shut-down-services}

모든 파일을 새 버전으로 바꾸려면 nlserver 서비스의 모든 인스턴스를 종료해야 합니다.

1. 다음 서비스를 종료합니다.

   * 웹 서비스(IIS):

      **iisreset /stop**

   * Adobe Campaign 서비스: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >또한 리디렉션 서버(webmdl)가 중지되었는지 확인하여 **nlsrvmod.dll** iis에서 사용하는 파일을 새 버전으로 바꿀 수 있습니다.

1. 를 실행하여 활성화된 작업이 없는지 확인 **nlserver 덤프** 명령입니다. 다음이 표시됩니다.

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Windows 작업 관리자를 사용하여 모든 프로세스가 중지되었는지 확인할 수 있습니다.

### Adobe Campaign 서버 애플리케이션 업그레이드 {#upgrade-the-adobe-campaign-server-application}

업그레이드 파일을 실행하려면 다음 단계를 적용합니다.

1. 실행 **setup.exe**.

   이 파일을 다운로드하려면 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 사용자 자격 증명을 사용합니다. 에서 소프트웨어 배포에 대해 자세히 알아보기 [이 페이지](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko).

1. 설치 모드 선택: 선택 **[!UICONTROL Update or repair]**
1. **[!UICONTROL Next]**&#x200B;를 클릭합니다.
1. **[!UICONTROL Finish]**&#x200B;를 클릭합니다.

   그런 다음 설치 프로그램이 새 파일을 복사합니다.

1. 작업이 완료되면 다음을 클릭합니다. **[!UICONTROL Finish]** .

### 리소스 동기화 {#synchronize-resources}

다음 명령줄을 사용하십시오.

**nlserver 구성 -업그레이드 후 -allinstances**

이렇게 하면 다음 작업을 수행할 수 있습니다.

* 리소스 동기화
* 스키마 업데이트
* 데이터베이스 업데이트

>[!NOTE]
>
>이 작업은 한 번만 수행해야 하며, (**nlserver 웹**) 응용 프로그램 서버입니다.

그런 다음 동기화에서 오류 또는 경고가 생성되었는지 확인합니다. 자세한 내용은 다음을 참조하십시오. [업그레이드 충돌 해결](#resolving-upgrade-conflicts).

### 서비스 다시 시작 {#restart-services}

다시 시작할 서비스는 다음과 같습니다.

* 웹 서비스(IIS):

   **iisreset /start**

* Adobe Campaign 서비스: **net start nlserver6**

## 리눅스 {#in-linux}

Linux 환경에서 아래 단계에 따라 Adobe Campaign을 새 빌드로 업데이트합니다.

* [업데이트된 패키지 다운로드](#obtain-updated-packages),
* [업데이트 수행](#perform-an-update),
* [웹 서버 재부팅](#reboot-the-web-server).

[클라이언트 콘솔 가용성에 대해 자세히 알아보기](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>빌드 8757부터 타사 라이브러리가 더 이상 필요하지 않습니다.

### 업데이트된 패키지 가져오기 {#obtain-updated-packages}

Adobe Campaign의 업데이트된 두 패키지를 모두 복구하여 시작: [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 사용자 자격 증명을 사용합니다. 에서 소프트웨어 배포에 대해 자세히 알아보기 [이 페이지](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko).

파일은 입니다. **nlserver6-v7-XXX.rpm**

### 업데이트 수행 {#perform-an-update}

* RPM 기반 배포(RedHat, SuSe)

   설치하려면 루트로 를 실행합니다.

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   여기서 XXX는 파일의 버전입니다.

   rpm 파일은 CentOS/Red Hat 배포판에서 찾을 수 있는 패키지에 종속되어 있습니다. 이러한 종속성 중 일부를 사용하지 않으려면 rpm의 &quot;nodeps&quot; 옵션을 사용해야 할 수 있습니다.

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* DEB 기반 분포(Debian)

   설치하려면 루트로 를 실행합니다.

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>전체 설치 절차는에 자세히 설명되어 있습니다. [이 섹션](../../installation/using/installing-campaign-standard-packages.md). 리소스는 자동으로 동기화되지만 오류가 발생하지 않았는지 확인해야 합니다. 자세한 내용은 다음을 참조하십시오. [업그레이드 충돌 해결](#resolving-upgrade-conflicts).

### 웹 서버 재부팅 {#reboot-the-web-server}

새 라이브러리를 적용하려면 Apache를 종료해야 합니다.

이렇게 하려면 다음 명령을 실행합니다.

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 스크립트를 호출할 수 있습니다. **httpd** 대신 **apache**.
>* 다음 회신을 받을 때까지 이 명령을 실행해야 합니다.

   >
   >   Apache가 새 라이브러리를 적용하려면 이 작업이 필요합니다.


그런 다음 Apache를 다시 시작합니다.

```
/etc/init.d/apache start
```

## 업그레이드 충돌 해결 {#resolving-upgrade-conflicts}

리소스를 동기화하는 동안 **업그레이드 후** 명령을 사용하면 동기화에서 오류 또는 경고가 생성되었는지 여부를 감지할 수 있습니다.

### 동기화 결과 보기 {#view-the-synchronization-result}

동기화 결과를 보는 방법에는 두 가지가 있습니다.

* 명령줄 인터페이스에서는 트리플 V자형 V자형 V자형 V자형으로 오류가 나타납니다 **>>>** 동기화가 자동으로 중지됩니다. 경고는 이중 V자형 화살표로 표시됩니다 **>>** 동기화가 완료되면 및 을(를) 해결해야 합니다. 업그레이드 후 요약이 명령 프롬프트에 표시됩니다. 다음과 같이 표시될 수 있습니다.

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   경고가 리소스 충돌과 관련된 경우 이를 해결하기 위해 사용자의 주의가 필요합니다.

* 다음 **업그레이드 후_`<server version number>_<time of postupgrade>`.log** 로그 파일에 동기화 결과가 포함되어 있습니다. 기본적으로 다음 디렉터리에서 사용할 수 있습니다. **`<installation directory>/var/<instance/postupgrade`**. 오류 및 경고는 오류 및 경고 속성으로 표시됩니다.

### 충돌 해결 {#resolving-conflicts}

충돌을 해결하려면 다음 프로세스를 적용합니다.

1. Adobe Campaign 트리에서 로 이동합니다. **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. 목록에서 해결할 충돌을 선택합니다.

충돌을 해결하는 방법에는 세 가지가 있습니다.

* **[!UICONTROL Declare as resolved]** : 사전에 사용자 개입이 필요합니다.
* **[!UICONTROL Accept the new version]** : Adobe Campaign과 함께 제공된 리소스가 사용자에 의해 변경되지 않은 경우 권장됩니다.
* **[!UICONTROL Keep the current version]** : 업데이트가 거부됨을 의미합니다.

   >[!IMPORTANT]
   >
   >이 해결 모드를 선택하면 새 버전에서 수정되지 않을 수 있습니다.

충돌을 수동으로 해결하도록 선택한 경우 다음과 같이 진행합니다.

1. 창의 아래쪽에서 **_충돌_** 문자열을 사용하여 충돌이 있는 엔티티를 찾습니다. 새 버전과 함께 설치된 엔티티에는 **신규** 인수, 이전 버전과 일치하는 엔터티에 **cus** 인수.

   ![](assets/s_ncs_production_conflict002.png)

1. 보관하지 않을 버전을 삭제합니다. 삭제 **_conflict_인수_** 유지할 엔터티의 문자열입니다.

   ![](assets/s_ncs_production_conflict003.png)

1. 해결한 충돌로 이동합니다. 다음을 클릭합니다. **[!UICONTROL Actions]** 아이콘 및 선택 **[!UICONTROL Declare as resolved]** .
1. 변경 내용을 저장합니다. 이제 충돌이 해결되었습니다.

### 모범 사례 {#best-practices}

업데이트 오류가 데이터베이스 구성에 연결되어 있을 수 있습니다. 기술 관리자와 데이터베이스 관리자가 수행한 구성이 호환되는지 확인합니다.

예를 들어 유니코드 데이터베이스는 LATIN1 데이터 등의 저장소만 허용해서는 안 됩니다.

## 사용 가능한 업데이트를 클라이언트 콘솔에 경고 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Adobe Campaign 애플리케이션 서버가 설치된 컴퓨터(**nlserver 웹**), 파일을 다운로드하고 복사합니다.  **setup-client-6.XXXX.exe** i n **[애플리케이션 경로]/datakit/nl/eng/jsp**.

다음 번에 클라이언트 콘솔이 연결되면 창은 사용자에게 업데이트 가용성에 대해 알리고 다운로드 및 설치 가능성을 제공합니다.

>[!NOTE]
>
>IIS_XPG 사용자에게 이 설치 파일에 대한 적절한 읽기 권한이 있는지 확인하고 [설치 안내서](../../installation/using/general-architecture.md) 추가 정보.

### 리눅스 {#in-linux-1}

Adobe Campaign 애플리케이션 서버(**nlserver 웹**)가 설치되어 있으면 를 검색합니다.  **setup-client-6.XXXX.exe** 패키지 및 복사, 다른 이름으로 저장 **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

다음 번에 클라이언트 콘솔이 연결되면 창은 사용자에게 업데이트 가용성에 대해 알리고 다운로드 및 설치 가능성을 제공합니다.

>[!NOTE]
>
>Apache 사용자에게 이 설치 파일에 대한 적절한 읽기 권한이 있는지 확인하고 [설치 안내서](../../installation/using/general-architecture.md) 추가 정보.
