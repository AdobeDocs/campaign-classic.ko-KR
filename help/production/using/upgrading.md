---
product: campaign
title: 새 빌드로 업그레이드
description: 새 빌드로 업그레이드하는 기술 단계를 배웁니다.
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 3%

---

# 새 빌드로 업그레이드(온-프레미스){#upgrading}



업그레이드 프로세스를 시작하기 전에 업그레이드할 Adobe Campaign 버전을 확인하고 를 참조하십시오. [릴리스 노트](../../rn/using/latest-release.md) .

>[!IMPORTANT]
>
>* Adobe은 업데이트하기 전에 각 인스턴스에 데이터베이스 백업을 수행하는 것이 좋습니다. 자세한 정보는 [이 섹션](../../production/using/backup.md)을 참조하십시오.
>* 업그레이드를 수행하려면 인스턴스 및 로그에 액세스할 수 있는 기능과 권한이 있는지 확인하십시오.
>* 읽기 [이 섹션](../../installation/using/general-architecture.md) 그리고 [빌드 업그레이드](https://helpx.adobe.com/kr/campaign/kb/acc-build-upgrade.html) 시작하기 전 장.
>


## Windows {#in-windows}

Windows 환경에서 아래 절차에 따라 Adobe Campaign을 새 빌드로 업데이트하십시오.

* [서비스 종료](#shut-down-services),
* [애플리케이션 서버 업그레이드](#upgrade-the-adobe-campaign-server-application),
* [리소스 동기화](#synchronize-resources),
* [서비스 다시 시작](#restart-services).

클라이언트 콘솔을 업데이트하는 방법을 알아보려면 [이 섹션](../../installation/using/client-console-availability-for-windows.md).

### 서비스 종료 {#shut-down-services}

모든 파일을 새 버전으로 바꾸려면 nlserver 서비스의 모든 인스턴스를 종료해야 합니다.

1. 다음 서비스를 종료합니다.

   * 웹 서비스(IIS):

      **isreset /stop**

   * Adobe Campaign 서비스: **net stop nlserver6**
   >[!IMPORTANT]
   >
   >또한 리디렉션 서버(webmdl)가 중지되어 **nlsrvmod.dll** IIS에서 사용하는 파일은 새 버전으로 대체할 수 있습니다.

1. 를 실행하여 활성 작업이 없는지 확인합니다. **nlserver pdump** 명령. 다음 내용이 표시됩니다.

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   Windows 작업 관리자를 사용하여 모든 프로세스가 중지되었는지 확인할 수 있습니다.

### Adobe Campaign 서버 애플리케이션 업그레이드 {#upgrade-the-adobe-campaign-server-application}

업그레이드 파일을 실행하려면 다음 단계를 수행합니다.

1. 실행 **setup.exe**.

   이 파일을 다운로드하려면 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 사용자 자격 증명 사용. 의 소프트웨어 배포에 대해 자세히 알아보십시오 [이 페이지](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko?lang=en).

1. 설치 모드를 선택합니다. 선택 **[!UICONTROL Update or repair]**
1. **[!UICONTROL Next]**&#x200B;를 클릭합니다.
1. **[!UICONTROL Finish]**&#x200B;를 클릭합니다.

   그런 다음 설치 프로그램이 새 파일을 복사합니다.

1. 작업이 완료되면 을 클릭합니다. **[!UICONTROL Finish]** .

### 리소스 동기화 {#synchronize-resources}

다음 명령줄을 사용합니다.

**nlserver 구성 -postupgrade -allinstances**

이렇게 하면 다음 작업을 수행할 수 있습니다.

* 리소스 동기화
* 스키마 업데이트
* 데이터베이스 업데이트

>[!NOTE]
>
>이 작업은 한 번만 수행되어야 하며 (**nlserver 웹**) 애플리케이션 서버를 포함할 수 없습니다.

그런 다음 동기화에 오류나 경고가 생성되었는지 확인합니다. 자세한 내용은 [업그레이드 충돌 해결](#resolving-upgrade-conflicts).

### 서비스 다시 시작 {#restart-services}

다시 시작할 서비스는 다음과 같습니다.

* 웹 서비스(IIS):

   **isreset /start**

* Adobe Campaign 서비스: **net start nlserver6**

## Linux {#in-linux}

Linux 환경에서 아래 절차에 따라 Adobe Campaign을 새 빌드로 업데이트하십시오.

* [업데이트된 패키지를 다운로드합니다](#obtain-updated-packages),
* [업데이트 수행](#perform-an-update),
* [웹 서버 다시 부팅](#reboot-the-web-server).

[클라이언트 콘솔 가용성에 대해 자세히 알아보기](../../installation/using/client-console-availability-for-windows.md).

>[!NOTE]
>
>빌드 8757에서 타사 라이브러리는 더 이상 필요하지 않습니다.

### 업데이트된 패키지 가져오기 {#obtain-updated-packages}

먼저 Adobe Campaign의 업데이트된 두 패키지를 모두 복구하십시오. 에 연결 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/ko/campaign.html) 사용자 자격 증명 사용. 의 소프트웨어 배포에 대해 자세히 알아보십시오 [이 페이지](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=ko?lang=en).

파일은 **nlserver6-v7-XXX.rpm**

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
>전체 설치 절차는 [이 섹션](../../installation/using/installing-campaign-standard-packages.md). 리소스는 자동으로 동기화되지만 오류가 발생하지 않았는지 확인해야 합니다. 자세한 내용은 [업그레이드 충돌 해결](#resolving-upgrade-conflicts).

### 웹 서버 다시 부팅 {#reboot-the-web-server}

새 라이브러리를 적용하려면 Apache를 종료해야 합니다.

이렇게 하려면 다음 명령을 실행합니다.

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 스크립트를 **httpd** 대신 **apache**.
>* 다음 응답을 받을 때까지 이 명령을 실행해야 합니다.

   >
   >   Apache가 새 라이브러리를 적용하려면 이 작업이 필요합니다.


그런 다음 Apache를 다시 시작합니다.

```
/etc/init.d/apache start
```

## 업그레이드 충돌 해결 {#resolving-upgrade-conflicts}

리소스를 동기화하는 동안 **postupgrade** 명령을 사용하면 동기화에 오류가 발생했는지 또는 경고가 발생했는지 감지할 수 있습니다.

### 동기화 결과 보기 {#view-the-synchronization-result}

동기화 결과를 보는 방법에는 두 가지가 있습니다.

* 명령줄 인터페이스에서 3중 V자형 화살표에 의해 오류가 나타납니다 **>>>** 동기화가 자동으로 중지됩니다. 이중 V자형 화살표에 의해 경고가 나타납니다 **>>** 동기화가 완료되면 및 를 해결해야 합니다. 업그레이드 후 종료 시 명령 프롬프트에 요약이 표시됩니다. 다음과 같이 표시될 수 있습니다.

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   경고 시 리소스 충돌이 발생할 경우 이를 해결하기 위해서는 사용자의 주의가 필요합니다.

* 다음 **postupgrade_`<server version number>_<time of postupgrade>`.log** 로그 파일에 동기화 결과가 포함되어 있습니다. 기본적으로 다음 디렉토리에서 사용할 수 있습니다. **`<installation directory>/var/<instance/postupgrade`**. 오류와 경고는 오류 및 경고 속성으로 표시됩니다.

### 충돌 해결 {#resolving-conflicts}

충돌을 해결하려면 다음 프로세스를 적용합니다.

1. Adobe Campaign 트리에서 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** .
1. 목록에서 해결할 충돌을 선택합니다.

분쟁을 해결하는 방법에는 세 가지가 있습니다.

* **[!UICONTROL Declare as resolved]** : 미리 사용자 개입이 필요합니다.
* **[!UICONTROL Accept the new version]** : 사용자가 Adobe Campaign과 함께 제공한 리소스를 변경하지 않은 경우 권장합니다.
* **[!UICONTROL Keep the current version]** : 은(는) 업데이트가 거부됨을 의미합니다.

   >[!IMPORTANT]
   >
   >이 해상도 모드를 선택하면 새 버전의 수정을 사용하지 못할 수 있습니다.

충돌을 수동으로 해결하도록 선택한 경우 다음과 같이 진행하십시오.

1. 창의 아래 섹션에서 **_충돌_** 충돌하는 엔티티를 찾기 위한 문자열입니다. 새 버전과 함께 설치된 엔티티에는 **새** 인수입니다. 이전 버전과 일치하는 엔티티는 **cus** 변합니다.

   ![](assets/s_ncs_production_conflict002.png)

1. 유지하지 않을 버전을 삭제합니다. 삭제 **_conflict_argument_** 유지할 엔티티의 문자열입니다.

   ![](assets/s_ncs_production_conflict003.png)

1. 해결된 충돌로 이동합니다. 을(를) 클릭합니다. **[!UICONTROL Actions]** 아이콘을 클릭하고 **[!UICONTROL Declare as resolved]** .
1. 변경 사항을 저장합니다. 이제 충돌이 해결되었습니다.

### 모범 사례 {#best-practices}

업데이트 실패 시 데이터베이스 구성에 연결할 수 있습니다. 기술 관리자 및 데이터베이스 관리자가 수행한 구성이 호환되는지 확인합니다.

예를 들어, 유니코드 데이터베이스는 LATIN1 데이터 등의 저장 권한을 부여해야 합니다.

## 사용 가능한 업데이트의 클라이언트 콘솔에 대해 경고 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

Adobe Campaign 애플리케이션 서버가 설치된 시스템(**nlserver 웹**), 파일을 다운로드하여 복사합니다.  **setup-client-6.XXXX.exe** i n **[애플리케이션의 경로]/datakit/nl/eng/jsp**.

다음에 클라이언트 콘솔이 연결되면 창에 업데이트 가용성에 대해 사용자에게 알리고 다운로드 및 설치 가능성을 제공합니다.

>[!NOTE]
>
>IIS_XPG 사용자에게 이 설치 파일에 대한 적절한 읽기 권한이 있는지 확인하고 다음을 참조하십시오. [설치 안내서](../../installation/using/general-architecture.md) 추가 정보.

### Linux {#in-linux-1}

Adobe Campaign 애플리케이션 서버(**nlserver 웹**)이 설치되면 검색합니다.  **setup-client-6.XXXX.exe** 패키지 및 복사 **/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

다음에 클라이언트 콘솔이 연결되면 창에 업데이트 가용성에 대해 사용자에게 알리고 다운로드 및 설치 가능성을 제공합니다.

>[!NOTE]
>
>Apache 사용자에게 이 설치 파일에 대한 적절한 읽기 권한이 있는지 확인하고 를 참조하십시오. [설치 안내서](../../installation/using/general-architecture.md) 추가 정보.
