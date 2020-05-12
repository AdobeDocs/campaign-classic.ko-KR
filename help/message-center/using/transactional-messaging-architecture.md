---
title: Adobe Campaign Classic 트랜잭션 메시징 아키텍처
description: 이 섹션에서는 Adobe Campaign Classic 트랜잭션 메시징 아키텍처에 대해 설명합니다.
page-status-flag: never-activated
uuid: a8fe7a37-6df7-49f4-838f-97a72e4a38f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: introduction
discoiquuid: a910d5fe-cef4-47d8-b3bc-0055ef0d1afd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e8a9d8d63c01cc19380267fced45e180b4d7ccb4
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---


# 트랜잭션 메시징 아키텍처{#transactional-messaging-architecture}

## 실행 및 제어 인스턴스 정보 {#about-execution-and-control-instances}

Adobe Campaign에서 트랜잭션 메시징 기능(메시지 센터라고도 함)은 확장성을 지원하고 24시간 연중무휴 서비스를 제공하도록 설계되었습니다. 여러 가지 인스턴스로 구성됩니다.

* 메시지 템플릿이 만들어지는 제어 인스턴스
* 이벤트를 받고 메시지를 전달하는 하나 이상의 실행 인스턴스.

이러한 기능을 사용하려면 제어 인스턴스에 로그인하여 트랜잭션 메시지 템플릿을 만들고, 시드 목록을 사용하여 메시지 미리 보기를 생성하고, 보고서를 표시하고 실행 인스턴스를 모니터링합니다.

실행 인스턴스는 이벤트를 수신하고, 트랜잭션 메시지 템플릿에 연결하고, 각 수신자에게 개인화된 메시지를 보냅니다.

![](assets/messagecenter_diagram.png)

## 여러 컨트롤 인스턴스 지원 {#supporting-several-control-instances}

>[!CAUTION]
>
>여러 제어 인스턴스와 실행 클러스터를 공유하는 것은 온-프레미스 환경에서만 지원됩니다.

여러 제어 인스턴스 간에 실행 클러스터를 공유할 수 있습니다. 예를 들어, 여러 전문 스토어를 관리하는 경우, 브랜드당 하나의 제어 인스턴스를 구성하고 모두 동일한 실행 클러스터에 연결할 수 있습니다.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>필요한 구성에 대한 자세한 내용은 여러 제어 인스턴스 [사용을 참조하십시오](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances).

## 인스턴스 설치 {#installing-instances}

트랜잭션 메시지 패키지를 설치할 때 몇 가지 주의사항이 있습니다. 프로덕션에 투입하기 전에 테스트 환경에서 작업하는 것이 좋습니다. 또한 호환되는 Adobe Campaign 라이선스가 있어야 합니다. 자세한 내용은 Adobe 계정 담당자에게 문의하십시오.

>[!CAUTION]
>
>제어 인스턴스와 실행 인스턴스를 다른 컴퓨터에 설치해야 합니다. 동일한 캠페인 인스턴스를 공유할 수 없습니다.

여러 채널을 사용해야 하는 경우 Transactional 메시지 패키지를 설치하기 전에 관련 패키지를 설치하고 구성해야 합니다. 전달 채널 [추가를 참조하십시오](#adding-a-delivery-channel).

* 컴퓨터에 제어 인스턴스를 설치하려면 **[!UICONTROL Transactional message control]** 모듈을 선택합니다.

   ![](assets/messagecenter_install_controlinstance_001.png)

* 컴퓨터에 실행 인스턴스를 설치하려면 **[!UICONTROL Transactional message execution]** 모듈을 선택합니다.

   ![](assets/messagecenter_install_executioninstance_001.png)

## 배달 채널 추가 {#adding-a-delivery-channel}

전달 채널 추가(모바일 채널, 모바일 앱 채널 등) 트랜잭션 메시지 패키지를 설치하기 전에 수행해야 합니다. 이메일 채널에서 트랜잭션 메시징 프로젝트를 시작한 다음 프로젝트 중에 새 채널을 추가하도록 결정하는 경우 다음 단계를 따라야 합니다.

1. 패키지 가져오기 마법사( **)를 사용하여 필요한 채널(예:**&#x200B;모바일 채널 **[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** )을 설치합니다.
1. 파일 가져오기( **[!UICONTROL Tools > Advanced > Import package... > File]** )를 수행하고 ****`[Your language]`**datakitnmackagemessageCenter.xml** 파일을 선택합니다.
1. 에서 **[!UICONTROL XML content of the data to import]** 추가된 채널에 해당하는 배달 템플릿만 유지합니다. 예를 들어 **모바일 채널을**&#x200B;추가한 경우 문자 **(smsTriggerMessage)에 해당하는** 엔티티 **[!UICONTROL Mobile transactional message]** 요소만유지합니다. 모바일 앱 채널을 추가한 경우 **iOS 트랜잭션 메시지**(iosTriggerMessage) 및 **Android 트랜잭션 메시지** (androidTriggerMessage)만 **** 보관하십시오.

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!CAUTION]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

## 트랜잭션 메시지 및 푸시 알림 {#transactional-messaging-and-push-notifications}

모바일 앱 채널 모듈과 결합하면 트랜잭션 메시지를 통해 모바일 장치의 알림을 통해 트랜잭션 메시지를 푸시할 수 있습니다.

>[!NOTE]
>
>모바일 앱 채널은 [이 섹션에 자세히 설명되어 있습니다](../../delivery/using/about-mobile-app-channel.md).

모바일 앱 채널에서 트랜잭션 메시지 모듈을 사용하려면 다음 구성을 적용해야 합니다.

1. 컨트롤 및 실행 인스턴스에 **모바일** 앱 채널 패키지를 설치합니다.
1. 실행 인스턴스에 포함된 **모바일 응용 프로그램** 유형 Adobe Campaign 서비스 및 모바일 응용 프로그램을 복제합니다.

이벤트에는 다음 요소가 포함되어야 합니다.

* 모바일 장치 ID(**Android** 및 iOS용 **deviceToken** ). 이 ID는 알림을 보낼 &quot;주소&quot;를 나타냅니다.
* 응용 프로그램과 관련된 연결 정보를 복구할 수 있는 모바일 응용 프로그램 또는&#x200B;**통합 키**(uuid)에 대한 링크입니다.
* 알림을 보낼 채널(**wishChannel**): iOS용 41 및 Android용 42
* 개인화에 유용한 모든 데이터

다음은 이 정보를 포함하는 이벤트의 예입니다.

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>메시지 템플릿 만들기는 동일하게 유지됩니다.

## 트랜잭션 메시지 및 LINE {#transactional-messaging-and-line}

LINE Channel과 함께 트랜잭션 메시지를 사용하면 일반 모바일 디바이스에 설치된 LINE 앱에서 실시간 메시지를 보낼 수 있습니다. LINE 사용자가 브랜드 페이지를 추가할 때 환영 메시지를 보내는 데 사용됩니다.

LINE과 함께 트랜잭션 메시지 모듈을 사용하려면 **마케팅** 인스턴스 및 **실행** 인스턴스의 구성에 다음 요소가 필요합니다.

* 두 인스턴스 모두에 **[!UICONTROL LINE Connect]** 패키지를 설치합니다.
* 마케팅 인스턴스에 **[!UICONTROL Transactional message control]** 패키지를 설치하고 실행 인스턴스에 패키지를 **[!UICONTROL Transactional message execution]** 설치합니다.
* 동일한 이름을 사용하여 두 인스턴스에 LINE **외부 계정** 및 **서비스를** 생성하여 동기화할 수 있습니다. LINE 외부 계정 및 서비스를 만드는 방법에 대한 자세한 내용은 이 [페이지를 참조하십시오](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-).

그런 다음 , **[!UICONTROL Explorer]****[!UICONTROL Platform]** > **[!UICONTROL External account]** 에서 두 인스턴스에 대해 다른 외부 계정을 구성해야 합니다.

1. 다음 구성을 사용하여 **[!UICONTROL External database]** 실행 **인스턴스에** 외부 계정을 만듭니다.

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** and **[!UICONTROL Internal name]** : 필요에 따라 외부 계정 이름을 지정합니다.
   * **[!UICONTROL Type]** : 선택 **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** 확인란을 선택해야 합니다.
   범주에서 **[!UICONTROL Connection]** 다음을 수행합니다.

   * **[!UICONTROL Type]** : 데이터베이스 서버(예: PostgresSQL)를 선택합니다.
   * **[!UICONTROL Server]** : 데이터베이스 서버 URL을 입력합니다.
   * **[!UICONTROL Account]** : 데이터베이스 계정을 입력합니다.

      >[!NOTE]
      >
      >FDA 연결을 위해서는 데이터베이스 사용자가 다음 표에 대한 읽기 권한이 있어야 합니다. XtkOption, NmsVisitor, NmsVisitorSub, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsNmsEvent RtEvent, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder를 참조하십시오.

   * **[!UICONTROL Password]** : 데이터베이스 계정의 암호를 입력합니다.
   * **[!UICONTROL Database]** : 실행 인스턴스의 데이터베이스 이름을 입력합니다.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** 확인란을 선택해야 합니다.


1. 다음 구성을 사용하여 **[!UICONTROL External Database]** 마케팅 **** 인스턴스에서 계정을 만듭니다.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** and **[!UICONTROL Internal name]** : 필요에 따라 외부 계정 이름을 지정합니다.
   * **[!UICONTROL Type]** : 선택 **[!UICONTROL External database]** .
   * 활성화 상자를 선택해야 합니다.
   범주에서 **[!UICONTROL Connection]** 다음을 수행합니다.

   * **[!UICONTROL Type]** : 선택 **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : 실행 인스턴스의 캠페인 서버 URL을 입력합니다.
   * **[!UICONTROL Account]** : 실행 인스턴스에 액세스하는 데 사용되는 계정을 입력합니다.
   * **[!UICONTROL Password]** : 실행 인스턴스에 액세스하는 데 사용되는 계정의 암호를 입력합니다.
   * **[!UICONTROL Data Source]** : 다음 구문을 입력합니다 **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** .


1. 다음 구성을 사용하여 **[!UICONTROL Execution instance]** 마케팅 **인스턴스에서** 외부 계정을 만들어 데이터 동기화 워크플로우를 생성합니다.

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** and **[!UICONTROL Internal name]** : 필요에 따라 외부 계정 이름을 지정합니다.
   * **[!UICONTROL Type]** : 선택 **[!UICONTROL Execution instance]** .
   * 활성화 상자를 선택해야 합니다.
   범주에서 **[!UICONTROL Connection]** 다음을 수행합니다.

   * **[!UICONTROL URL]** : 실행 인스턴스의 URL을 입력합니다.
   * **[!UICONTROL Account]** : 실행 인스턴스에 액세스하는 데 사용한 계정을 입력합니다.
   * **[!UICONTROL Password]** : 실행 인스턴스에 액세스하는 데 사용되는 계정의 암호를 입력합니다.
   범주에서 **[!UICONTROL Account connection method]** 다음을 수행합니다.

   * **[!UICONTROL Method]** : 선택 **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : 드롭다운에서 FDA 계정을 선택합니다.
   * 단추를 **[!UICONTROL Create the archiving workflow]** 클릭합니다.
   * 이 **[!UICONTROL Create data synchronization workflow]** 단추를 클릭하여 LINE 데이터 동기화 워크플로우를 만듭니다.



1. 이제 트랜잭션 메시지 작성을 시작할 수 있습니다. 자세한 내용은 이 [페이지를 참조하십시오](../../message-center/using/introduction.md).
