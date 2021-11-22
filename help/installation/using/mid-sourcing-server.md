---
product: campaign
title: Campaign에서 중간 소싱 서버 설치
description: 이 섹션에서는 Campaign에서 중간 소싱 서버의 설치 및 구성에 대해 자세히 설명합니다
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 3e55d7f5-2858-4390-bba9-8fb5be0c3d98
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '999'
ht-degree: 1%

---

# 중간 소싱 서버{#mid-sourcing-server}

![](../../assets/v7-only.svg)

이 섹션에서는 중간 소싱 서버의 설치 및 구성과 타사에서 메시지를 보낼 수 있는 인스턴스의 배포에 대해 자세히 설명합니다 **중간 소싱** 모드.

중간 소싱 아키텍처는 [중간 소싱 배포](../../installation/using/mid-sourcing-deployment.md).

중간 소싱 서버 설치는 일반적인 방법으로 서버를 설치하는 것과 동일한 프로세스를 따릅니다(표준 구성 참조). 자체 데이터베이스가 있는 독립 인스턴스이며, 게재를 실행하는 데 사용할 수 있습니다. 즉, 중간 소싱 모드에서 원격 인스턴스가 게재를 통해 게재를 실행할 수 있도록 추가 구성이 포함되어 있습니다.

>[!CAUTION]
>
>중간 소싱 서버를 설정하고 [워크플로우 동기화](../../workflow/using/about-technical-workflows.md) 가 처음 실행되었는지 확인합니다. 중간 소싱 외부 계정의 내부 이름을 업데이트하지 않는지 확인합니다.

## 인스턴스 설치 및 구성 단계 {#steps-for-installing-and-configuring-an-instance}

### 인스턴스 설치 및 구성을 위한 사전 요구 사항 {#prerequisites-for-installing-and-configuring-an-instance}

* 애플리케이션 서버의 JDK입니다.
* 응용 프로그램 서버의 데이터베이스 서버에 액세스합니다.
* 중간 소싱 서버로 HTTP(80) 또는 HTTPS(443) 포트를 열도록 방화벽이 구성되어 있습니다.

다음 절차에서는 단일 중간 소싱 서버를 사용하는 구성에 대해 자세히 설명합니다. 여러 서버를 사용할 수도 있습니다. 마찬가지로 내부 구성에서 특정 메시지(예: 워크플로우 알림 등)를 전송할 수도 있습니다.

### 중간 소싱 배포를 위한 애플리케이션 서버 설치 및 구성 {#installing-and-configuring-the-application-server-for-mid-sourcing-deployment}

설치 프로시저는 독립형 인스턴스의 절차와 동일합니다. 을(를) 참조하십시오. [설치 및 구성(단일 시스템)](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-).

그러나 다음을 적용해야 합니다.

* 단계 **5개**, 을 비활성화해야 합니다 **mta** (게재) 및 **inMail** (바운스 메일) 모듈입니다. 다음 **wfserver** (워크플로우) 모듈은 계속 활성화되어야 합니다.

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

   이 작업에 대한 자세한 정보는 [이 섹션](../../installation/using/configuring-campaign-server.md#enabling-processes)을 참조하십시오.

* 단계 **6**, **9** 및 **10** 필요하지 않습니다.
* 단계 중 **12** 및 **13**&#x200B;를 채울 때는 연결 URL에 8080 포트를 표시해야 합니다. 콘솔이 웹 서버가 아닌 Tomcat과 직접 통신하므로 이 포트를 표시해야 합니다. URL은 [http://console.campaign.net:8080](http://console.campaign.net). 단계 중 **13**&#x200B;에서 을(를) 선택합니다. **[!UICONTROL Issue towards Mid-sourcing]** 패키지 및 설치할 패키지입니다.

   ![](assets/s_ncs_install_midsourcing02.png)

   >[!CAUTION]
   >
   >기술 게재의 기본 라우팅은 중간 소싱을 통해 전자 메일 라우팅으로 자동 대체됩니다.

### 중간 소싱 서버 설치 및 구성 {#installing-and-configuring-the-mid-sourcing-server}

클라이언트 콘솔에서 를 찾습니다. **중간 소싱을 사용한 전자 메일 라우팅** 중간 소싱 계정( **/관리/외부 계정/** 폴더). 을(를) 채우기 **서버의 URL**, **account**, **암호** 및 **미러 페이지 URL** 중간 소싱 서버를 호스팅하는 서버 공급자가 제공하는 정보를 사용하는 설정입니다. 연결을 테스트합니다.

>[!NOTE]
>
>다음 **mid-sourcingEmitter** 옵션을 두 개 만듭니다. **중간 소싱** 워크플로우. 기본적으로 1시간 20분마다 실행되고 중간 소싱 서버에서 게재 정보를 수집하는 프로세스입니다.

## 중간 소싱 서버 배포 {#deploying-a-mid-sourcing-server}

1. 애플리케이션 서버 설치:

   >[!CAUTION]
   >
   >중간 소싱 서버를 설치하고 추가 Adobe Campaign 모듈을 설치하려면 캠페인 모듈이 아니라 게재 모듈을 사용하는 것이 좋습니다.

   표준 배포와 동일한 절차에 따라 다음 항목만 선택합니다 **[!UICONTROL Mid-sourcing platform]** 선택 사항입니다.

   ![](assets/s_ncs_install_midsourcing01.png)

1. 중간 소싱 모드에서 수신하기 위한 구성

   제출 계정 암호를 설정합니다. 에서 **/중간 소싱/액세스 관리/운영자/** 폴더, **mid** 중간 소싱 모드에서 제출을 위해 원격 인스턴스에서 연산자를 사용합니다. 이 연산자에 대한 암호를 설정하고 제출 인스턴스의 관리자에게 제공해야 합니다.

   다음 **중간 소싱 플랫폼** 옵션을 사용하면 제출된 게재를 저장할 기본 폴더가 생성되고 제출을 수행하는 기본 연산자가 생성됩니다.

## 중간 소싱 서버 멀티플렉싱 {#multiplexing-the-mid-sourcing-server}

>[!CAUTION]
>
>멀티플렉싱은 온-프레미스 환경에서만 지원됩니다.

중간 소싱 인스턴스를 여러 제출 인스턴스로 공유할 수 있습니다. 이러한 각 인스턴스는 중간 소싱 데이터베이스의 연산자와 연결되어야 합니다. 중간 소싱 서버에서 두 번째 계정을 생성하려면

1. 에서 폴더 만들기 **[!UICONTROL Mid-sourcing > Deliveries]** 기본 중간 소싱 계정과 연결된 노드(예: prod)에 속해 있어야 합니다.
1. 에서 폴더 만들기 **[!UICONTROL Mid-sourcing > Deliveries]** 계정과 동일한 이름을 가진 노드(예: accept_test).

   ![](assets/mid_recette_account.png)

1. in **[!UICONTROL Mid-sourcing > Access Management > Operators]**&#x200B;새 계정을 만듭니다.

   ![](assets/mid_recette_user_create.png)

1. 에서 **[!UICONTROL Access rights]** 탭에서 이 연산자에게 **중간 소싱 제출** 그룹에 속해 있어야 합니다. 이 액세스 권한은 **[!UICONTROL Mid-sourcing > Access Management > Operator groups]**.

   ![](assets/mid_recette_user_rights.png)

1. 을(를) 선택합니다 **[!UICONTROL Restrict to data in the sub-folders of]** 옵션을 선택하고 이 연산자를 중간 소싱 게재 폴더로 제한하려면 게재 폴더를 선택합니다.

   ![](assets/mid_recette_user_restrictions.png)

1. 다음 명령을 사용하여 웹 모듈을 다시 시작합니다. **nlserver 다시 시작 웹**.

serverConf.xml 파일에서 중간 소싱 서버 설정을 변경해야 합니다. 기존 라인 아래의 &quot;IP 주소가 있는 관심 영역 관리&quot; 섹션에 다음 줄을 추가해야 합니다.

```
<IPAffinity IPMask="" localDomain="" name=""/>
```

&#39;@name&#39; 속성은 다음 규칙을 준수해야 합니다.

**&#39;marketing_account_operator_name&#39;affinity_name&#39;입니다.&#39;affinity_group&#39;**

&#39;marketing_account_operator_name&#39;은 중간 소싱 인스턴스에서 선언된 중간 소싱 계정의 내부 이름에 대한 것입니다.

&#39;affinity_name&#39;은 친화성에 지정된 임의 이름과 관련이 있습니다. 이 이름은 고유해야 합니다. 인증된 문자는 `[a-z]``[A-Z]``[0-9]`. 그 목적은 공용 IP 주소 그룹을 선언하는 것이다.

&#39;affinity_group&#39;은 각 게재에 사용되는 대상 매핑에서 선언된 하위 친화성을 관계가 있습니다. &#39;.&#39;를 포함하는 마지막 부분 하위 친화성이 없으면 가 무시됩니다. 인증된 문자는 `[a-z]``[A-Z]``[0-9]`.

수정을 고려하려면 서버를 중지한 다음 다시 시작해야 합니다.

## 중간 소싱 서버에서 추적 구성 {#configuring-tracking-on-a-mid-sourcing-server}

**중간 소싱 서버 구성**

1. &#39;연산자&#39;로 이동하고 연산자를 선택합니다 **[!UICONTROL mid]**.
1. 에서 **[!UICONTROL Frontal servers]** 탭에서 추적 서버 연결 매개 변수를 입력합니다.

   추적 인스턴스를 생성하려면 추적 서버의 URL, 추적 서버 내부 계정 암호 및 인스턴스 이름, 해당 암호 및 추적 서버와 연관된 DNS 마스크를 입력합니다.

   ![](assets/s_ncs_install_midsourcing_tracking02.png)

1. 연결 매개 변수를 입력한 경우 **[!UICONTROL Confirm the configuration]**.
1. 필요한 경우 게재에 포함된 이미지를 저장할 위치를 지정합니다. 이렇게 하려면 드롭다운 목록에서 게시 모드 중 하나를 선택합니다.

   ![](assets/s_ncs_install_midsourcing_tracking03.png)

   을(를) 선택하는 경우 **[!UICONTROL Tracking server(s)]** 옵션을 선택하면 중간 소싱 서버에 이미지가 복사됩니다.

**고객 플랫폼 구성**

1. 외부 중간 소싱 공정순서 계정으로 이동합니다.
1. 에서 **[!UICONTROL Mid-Sourcing]** 탭에서 중간 소싱 서버 연결 매개 변수를 지정합니다.

   ![](assets/s_ncs_install_midsourcing_tracking06.png)

1. 다음을 클릭하여 구성을 확인합니다 **[!UICONTROL Test the connection]**.
1. 중간 소싱 서버에서 참조되는 추적 인스턴스를 선언합니다.

   링크를 클릭합니다 **[!UICONTROL Use this platform as a proxy to access the tracking servers]**,

   추적 인스턴스의 이름을 지정한 다음 추적 서버와의 연결을 확인합니다.

   ![](assets/s_ncs_install_midsourcing_tracking05.png)

메시지 전달을 여러 중간 소싱 서버에서 관리하는 경우 옵션을 선택합니다 **[!UICONTROL Routing with alternating mid-sourcing accounts]** 다른 서버를 지정합니다.

![](assets/s_ncs_install_midsourcing_tracking04.png)
