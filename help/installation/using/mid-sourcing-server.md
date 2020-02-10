---
title: Adobe Campaign Classic에서 mid-sourcing 서버 설치
description: 이 섹션에서는 Adobe Campaign Classic에서 mid 소싱 서버의 설치 및 구성에 대해 자세히 설명합니다.
page-status-flag: never-activated
uuid: 9b891a64-d75e-44d2-8de2-17334e1b8dca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 34ee3d99-4ffb-4279-b994-5ab7abc7cf06
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 25ae29490f8b4c58dad499669f5bccff43de8b7a

---


# 중간 소싱 서버{#mid-sourcing-server}

이 섹션에서는 중간 소싱 서버의 설치 및 구성과 제3자가 **중간 소싱** 모드로 메시지를 전송할 수 있는 인스턴스의 배포에 대해 자세히 설명합니다.

&quot;mid-sourcing&quot; 아키텍처는 Mid-sourcing [배포에](../../installation/using/mid-sourcing-deployment.md)표시됩니다.

중간 소싱 서버를 설치하면 일반적인 방법으로 서버를 설치하는 것과 동일한 프로세스를 따릅니다(표준 구성 참조). 자체 데이터베이스가 있는 독립 인스턴스로서 전달을 실행하는 데 사용할 수 있습니다. 간단히 말해, 이 템플릿에는 중간 소싱 모드에서 원격 인스턴스가 전달을 실행할 수 있도록 추가 구성이 포함되어 있습니다.

## 인스턴스 설치 및 구성 단계 {#steps-for-installing-and-configuring-an-instance}

### 인스턴스 설치 및 구성을 위한 전제 조건 {#prerequisites-for-installing-and-configuring-an-instance}

* 응용 프로그램 서버의 JDK입니다.
* 응용 프로그램 서버에서 데이터베이스 서버에 액세스합니다.
* HTTP(80) 또는 HTTPS(443) 포트를 미드소싱 서버로 열도록 방화벽이 구성되었습니다.

다음 절차에서는 단일 mid-sourcing 서버를 사용하는 구성에 대해 자세히 설명합니다. 여러 서버를 사용할 수도 있습니다. 마찬가지로 내부 구성에서 특정 메시지(예: 워크플로우 알림)를 전송할 수도 있습니다.

### 중간 소싱 배포를 위한 애플리케이션 서버 설치 및 구성 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

설치 절차는 독립 실행형 인스턴스의 절차와 동일합니다. 설치 [및 구성(단일 시스템)을 참조하십시오](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

그러나 다음을 적용해야 합니다.

* 5단계에서 **** mta **(배달)와** inMail **(바운스 메일)** 모듈을비활성화해야 합니다. 그러나 **wfserver** (워크플로우) 모듈은 계속 활성화되어야 합니다.

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="false"/>  
       <wfserver autoStart="true"/>  
       <inMail autoStart="false"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   자세한 내용은 프로세스 [활성화를 참조하십시오](../../installation/using/campaign-server-configuration.md#enabling-processes).

* 6 **단계**, **9** 단계, **10단계는** 필요하지 않습니다.
* 12 **단계** 및 **13단계**&#x200B;중에 연결 URL에 8080 포트를 표시해야 합니다(콘솔이 웹 서버를 통해 직접 Tomcat과 통신하지 않으므로). URL은 http://console.campaign.net:8080가 [됩니다](http://console.campaign.net). 13 **단계에서**&#x200B;설치할 **[!UICONTROL Issue towards Mid-sourcing]** 패키지뿐만 아니라 패키지를 선택합니다.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >기술 납품의 기본 공정순서는 중간 소싱을 통해 이메일 공정순서로 자동 대체됩니다.

### 중간 소싱 서버 설치 및 구성 {#installing-and-configuring-the-mid-sourcing-server}

클라이언트 콘솔에서 중간 소싱 **mid-sourcing 계정(** /관리/외부 계정/ **** 폴더)을 사용하여 이메일 라우팅을 찾습니다. 서버 **,**&#x200B;계정 **,**&#x200B;암호 **및** **** 미러 페이지 URL의 URL을 미드소싱 서버를 호스팅하는 서버에서 제공하는 정보로 채웁니다. 연결을 테스트합니다.

>[!NOTE]
>
>mid-sourcingEmitter **옵션은 두** 가지 mid-sourcing **** 워크플로우를 생성합니다. 기본적으로 1시간 20분마다 실행되고 중간 소싱 서버에서 배달 정보를 수집하는 프로세스입니다.

## 중간 소싱 서버 배포 {#deploying-a-mid-sourcing-server}

1. 응용 프로그램 서버 설치:

   >[!CAUTION]
   >
   >중간 소싱 서버를 설치하고 추가 Adobe Campaign 모듈을 설치하려면 캠페인 모듈이 아닌 배달 모듈을 사용하는 것이 좋습니다.

   표준 배포와 동일한 절차에 따라 **[!UICONTROL Mid-sourcing platform]** 옵션만 선택합니다.

   ![](assets/s_ncs_install_midsourcing01.png)

1. 중간 소싱 모드에서 입고를 위한 구성

   제출 계정 암호를 설정합니다./Mid-sourcing/ **Access Management/Operators/** 폴더에서 **mid** 연산자는 mid-sourcing 모드에서 제출을 위해 원격 인스턴스에서 사용합니다. 이 연산자의 암호를 설정하고 제출 인스턴스의 관리자에게 제공해야 합니다.

   중간 **소싱 플랫폼** 옵션은 제출된 납품을 저장할 기본 폴더를 만들고 제출을 수행하는 기본 연산자를 만듭니다.

## 중간 소싱 서버 멀티플렉싱 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>멀티플렉싱은 온-프레미스 환경에서만 지원됩니다.

중간 소싱 인스턴스를 여러 제출 인스턴스로 공유할 수 있습니다. 이러한 각 인스턴스는 중간 소싱 데이터베이스의 연산자와 연관되어야 합니다. 중간 소싱 서버에서 두 번째 계정을 만들려면

1. 기본 mid-sourcing 계정과 연결될 **[!UICONTROL Mid-sourcing > Deliveries]** 노드에 폴더를 만듭니다(예:prod).
1. 계정과 동일한 이름으로 **[!UICONTROL Mid-sourcing > Deliveries]** 노드에 폴더를 만듭니다(예:acceptance_test).

   ![](assets/mid_recette_account.png)

1. 에서 **[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;새 계정을 만듭니다.

   ![](assets/mid_recette_user_create.png)

1. 이 **[!UICONTROL Access rights]** 탭에서 이 연산자에게 중간 소싱 제출 **그룹의 권한을 지정합니다** . 이 액세스 권한은 에서 사용할 수 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**&#x200B;있습니다.

   ![](assets/mid_recette_user_rights.png)

1. 이 연산자를 중간 소싱 납품 폴더로 제한하려면 **[!UICONTROL Restrict to data in the sub-folders of]** 옵션을 선택하고 배달 폴더를 선택합니다.

   ![](assets/mid_recette_user_restrictions.png)

1. 다음 명령을 사용하여 웹 모듈을 다시 시작합니다.서버를 **다시 시작합니다**.

serverConf.xml 파일에서 mid-sourcing 서버 설정을 변경해야 합니다. 다음 줄을 기존 줄의 &quot;IP 주소가 있는 친화성 관리&quot; 섹션에 추가해야 합니다.

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

&#39;@name&#39; 특성은 다음 규칙을 준수해야 합니다.

**&#39;marketing_account_operator_name&#39;affinity_name&#39;.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39;은 mid-sourcing 인스턴스에 선언된 mid-sourcing 계정의 내부 이름과 관련이 있습니다.

&#39;affinity_name&#39;은 선호도에 지정된 임의 이름과 관련됩니다. 이 이름은 고유해야 합니다. 공인 문자는 다음과 `[a-z]``[A-Z]``[0-9]`같습니다. 그 목적은 공개 IP 주소 그룹을 선언하는 것이다.

&#39;affinity_group&#39;은 각 게재에 사용된 대상 매핑에서 선언된 하위 친화성을 관련시킵니다. &#39;.&#39;를 포함한 마지막 부분 하위 친화성이 없으면 무시됩니다. 공인 문자는 다음과 `[a-z]``[A-Z]``[0-9]`같습니다.

수정을 고려하려면 서버를 중지한 다음 다시 시작해야 합니다.

## 중간 소싱 서버에서 추적 구성 {#configuring-tracking-on-a-mid-sourcing-server}

**중간 소싱 서버 구성**

1. &#39;연산자&#39;로 이동하여 연산자를 **[!UICONTROL mid]**&#x200B;선택합니다.
1. 탭에서 추적 서버 연결 매개 변수를 입력합니다. **[!UICONTROL Frontal servers]**

   추적 인스턴스를 만들려면 추적 서버의 URL, 추적 서버 내부 계정 암호 및 인스턴스 이름, 암호 및 추적 서버와 연결된 DNS 마스크를 입력합니다.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 연결 매개 변수를 입력했으면 을 **[!UICONTROL Confirm the configuration]**&#x200B;클릭합니다.
1. 필요한 경우 게재에 포함된 이미지를 저장할 위치를 지정합니다. 이렇게 하려면 드롭다운 목록에서 게시 모드 중 하나를 선택합니다.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   이 **[!UICONTROL Tracking server(s)]** 옵션을 선택하면 이미지가 mid-sourcing 서버에 복사됩니다.

**고객 플랫폼 구성**

1. 외부 소싱 공정순서 계정으로 이동합니다.
1. 이 **[!UICONTROL Mid-Sourcing]** 탭에서 중간 소싱 서버 연결 매개변수를 지정합니다.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 을 클릭하여 구성을 **[!UICONTROL Test the connection]**&#x200B;확인합니다.
1. 중간 소싱 서버에서 참조되는 추적 인스턴스를 선언합니다.

   링크를 **[!UICONTROL Use this platform as a platform to access the tracking servers]**&#x200B;클릭합니다.

   추적 인스턴스의 이름을 지정한 다음 추적 서버와의 연결을 확인합니다.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

메시지 전달을 여러 mid-sourcing 서버에서 관리하려면 옵션을 선택하고 다른 서버를 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 지정합니다.

![](assets/s_ncs_install_midsourcing_tracking04.png)

