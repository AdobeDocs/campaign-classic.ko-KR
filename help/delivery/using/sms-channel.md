---
title: SMS 채널
seo-title: SMS 채널
description: SMS 채널
seo-description: null
page-status-flag: never-activated
uuid: be6a2abc-ba5c-4363-bf38-cc309ee3a8d9
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
discoiquuid: 8b101c0b-3611-4f15-813b-7c0bf54fc48a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3bf835b3f686d1293fda7e6254660c477ba26452
workflow-type: tm+mt
source-wordcount: '3152'
ht-degree: 1%

---


# SMS 채널{#sms-channel}

Adobe Campaign을 사용하면 SMS 메시지를 개인화하여 전달할 수 있습니다. 받는 사람 프로필에 모바일 전화 번호 이상이 포함되어야 합니다.

>[!NOTE]
>
>또한 Adobe Campaign을 사용하면 **Adobe Campaign NMAC(Mobile App Channel) 옵션을 통해 모바일 터미널에 알림을 제출할 수** 있습니다.
> 
>자세한 내용은 모바일 앱 채널 [정보 섹션을 참조하십시오](../../delivery/using/about-mobile-app-channel.md) .

아래 섹션에서는 SMS 채널과 관련된 정보를 제공합니다. 배달을 만드는 방법에 대한 자세한 내용은[이 섹션을 참조하십시오](../../delivery/using/steps-about-delivery-creation-steps.md).

## SMS 채널 설정 {#setting-up-sms-channel}

휴대폰으로 전송하려면 다음이 필요합니다.

1. 커넥터 및 메시지 유형을 지정하는 외부 계정.

   다음 커넥터는 릴리스 20.2부터 더 이상 사용되지 않습니다. NetSize, 일반 SMPP(바이너리 모드 지원 SMPP 버전 3.4), Sybase365(SAP SMS 365), CLX Communications, Tele2, O2 및 iOS. 더 이상 사용되지 않는 기능은 여전히 사용할 수 있지만 더 이상 향상되거나 지원되지 않습니다. For more on this, refer to this [page](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html).

1. 이 외부 계정이 참조되는 배달 템플릿입니다.

### SMPP 외부 계정 만들기 {#creating-an-smpp-external-account}

휴대폰에 SMS를 보내려면 먼저 SMPP 외부 계정을 만들어야 합니다.
SMS 프로토콜 및 설정에 대한 자세한 내용은 이 [기술 문서를 참조하십시오](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html).

이렇게 하려면 아래 단계를 수행합니다:

1. 트리의 **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** 노드에서 **[!UICONTROL New]** 아이콘을 클릭합니다.
1. 계정 유형을 **라우팅**, 채널 **을**&#x200B;모바일(SMS) **및 배달 모드를**&#x200B;벌크 배달로 정의합니다.

   ![](assets/extended_smpp_create_account.png)

1. 체크 **[!UICONTROL Enabled]** 상자를
1. 탭의 **[!UICONTROL Mobile]** 드롭다운 목록 **[!UICONTROL Extended generic SMPP]** **[!UICONTROL Connector]** 에서 선택합니다.

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > 릴리스 20.2부터는 레거시 커넥터가 더 이상 지원되지 않습니다. 커넥터를 사용하는 것이 **[!UICONTROL Extended generic SMPP]** 좋습니다. 권장 커넥터로 마이그레이션하는 방법에 대한 자세한 내용은 이 [페이지를 참조하십시오](https://helpx.adobe.com/campaign/kb/sms-connector.html).

1. 이 **[!UICONTROL Enable verbose SMPP traces in the log file]** 옵션을 사용하면 모든 SMPP 트래픽을 로그 파일에 덤프할 수 있습니다. 커넥터를 해결하고 공급자가 보는 트래픽과 비교하려면 이 옵션을 활성화해야 합니다.

1. SMS 서비스 제공업체에 문의하여 **[!UICONTROL Connection settings]** 탭에서 다양한 외부 계정 필드를 완료하는 방법을 설명합니다.

   그런 다음 선택한 필드에 입력할 값을 제공하는 공급자에 따라 해당 공급자에게 **[!UICONTROL SMSC implementation name]** 문의하십시오.

   MTA 하위 항목당 공급자에 대한 연결 수를 정의할 수 있습니다. 기본적으로 1로 설정됩니다.

1. 기본적으로 SMS의 문자 수는 GSM 표준을 충족합니다.

   GSM 인코딩을 사용하는 SMS 메시지는 SMS당 160자, 즉 여러 부분으로 전송되는 메시지에 대해 SMS당 153자로 제한됩니다.

   >[!NOTE]
   >
   >특정 문자는 두 개(중괄호, 대괄호, 유로 기호 등)로 계산합니다.
   >
   >사용 가능한 GSM 문자 목록은 아래에 나와 있습니다.

   원하는 경우 해당 상자를 선택하여 문자 교환을 승인할 수 있습니다.

   ![](assets/extended_smpp_transliteration.png)

   이 작업에 대한 자세한 정보는 [이 섹션](#about-character-transliteration)을 참조하십시오.

1. In the **[!UICONTROL Throughput and delays]** tab, you can specify the maximum throughput of outbound messages (&quot;MT&quot;, Mobile Terminated) in MT per second. 해당 필드에 &quot;0&quot;을 입력하면 처리량이 무제한이 됩니다.

   기간에 해당하는 모든 필드의 값을 초 단위로 완료해야 합니다.

1. 탭에서 **[!UICONTROL Mapping of encodings]** 인코딩을 정의할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](#about-text-encodings)을 참조하십시오.

1. 이 **[!UICONTROL SMSC specificities]** 탭에서 **[!UICONTROL Send full phone number]** 옵션은 기본적으로 비활성화됩니다. SMPP 프로토콜을 존중하고 SMSC(SMS 공급자)의 서버에 숫자만 전송하려는 경우 활성화하지 마십시오.

   그러나 특정 공급업체에서 &#39;+&#39; 접두사를 사용해야 하는 경우 해당 공급자에게 확인하면 필요한 경우 이 옵션을 사용하도록 설정하는 것이 좋습니다.

   이 확인란을 **[!UICONTROL Enable TLS over SMPP]** 사용하면 SMPP 트래픽을 암호화할 수 있습니다. 자세한 내용은 이 [기술 문서를 참조하십시오](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html).

1. 커넥터를 구성하는 **[!UICONTROL Extended generic SMPP]** 경우 자동 답글을 설정할 수 있습니다.

   이 작업에 대한 자세한 정보는 [이 섹션](#automatic-reply)을 참조하십시오.

### 문자 변환 정보 {#about-character-transliteration}

SMPP 모바일 전달 외부 계정의 **[!UICONTROL Mobile]** 탭 아래에서 문자 변환 기능을 설정할 수 있습니다.

교역은 GSM 표준으로 문자를 고려하지 않은 경우 SMS의 한 문자를 다른 문자로 바꾸는 것으로 이루어집니다.

* 교역을 하는 경우 **[!UICONTROL authorized]**&#x200B;가 고려되지 않은 각 문자는 메시지를 보낼 때 GSM 문자로 대체됩니다. 예를 들어, &quot;레크&quot;는 &quot;e&quot;로 대체됩니다. 따라서 메시지는 약간 변경되지만 문자 제한은 그대로 유지됩니다.
* 음역법이 **[!UICONTROL not authorized]**&#x200B;설정되면, 고려하지 않은 문자가 포함된 각 메시지는 바이너리 형식(유니코드)으로 전송됩니다. 따라서 모든 문자가 있는 그대로 전송됩니다. 그러나 유니코드를 사용하는 SMS 메시지는 70자(또는 여러 부분으로 전송된 메시지의 경우 SMS당 67자)로 제한됩니다. 최대 문자 수가 초과되면 여러 개의 메시지가 전송되어 추가 비용이 발생할 수 있습니다.

>[!IMPORTANT]
>
>SMS 메시지의 컨텐츠에 개인화 필드를 삽입하면 GSM 인코딩에 의해 고려되지 않는 문자가 도입될 수 있습니다.

기본적으로 문자 음역은 비활성화됩니다. SMS 메시지의 모든 문자를 그대로 유지하려면 적절한 이름을 변경하지 않는 것이 좋습니다. 이 옵션을 활성화하지 않는 것이 좋습니다.

그러나 SMS 메시지에 유니코드 메시지를 생성하는 문자가 많이 포함된 경우 이 옵션을 활성화하여 메시지 전송 비용을 제한할 수 있습니다.

다음 표에서는 GSM 표준에서 다루는 문자를 보여 줍니다. 아래에 언급된 문자 외에 메시지 본문에 삽입된 모든 문자는 전체 메시지를 바이너리 형식(유니코드)으로 변환하여 70자로 제한합니다.

**기본 문자**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> ¡ </td> 
   <td> P </td> 
   <td> ¿ </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> 에 </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> ¤ </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> 우 </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> 2차 </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> 보 </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Bari </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> 쇠 </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ae </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> 5 </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> 멕시코산 </td> 
  </tr> 
  <tr> 
   <td> 오 </td> 
   <td> 성 </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> 여우 </td> 
   <td> n </td> 
   <td> 여우 </td> 
  </tr> 
  <tr> 
   <td> o </td> 
   <td> 에 </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: 공간

ESC: Escape

LF: 라인 피드

CR: 캐리지 리턴

**고급 문자(두 번 계산됨)**

^ { } `[ ~ ]` | €

### 텍스트 인코딩 정보 {#about-text-encodings}

SMS 메시지를 보낼 때 Adobe Campaign에서 하나 또는 여러 개의 텍스트 인코딩을 사용할 수 있습니다. 각 인코딩은 고유한 문자 집합을 가지며 SMS 메시지에 맞는 문자 수를 결정합니다.

새 SMPP 모바일 배달 외부 계정을 구성할 때 탭 **[!UICONTROL Mapping of encodings]** 에서 다음을 정의할 수 **[!UICONTROL Mobile]** 있습니다. 이 **[!UICONTROL data_coding]** 필드를 사용하면 Adobe Campaign에서 SMSC에 사용되는 인코딩을 통신할 수 있습니다.

>[!NOTE]
>
>data_coding **** 값과 실제로 사용된 인코딩 간의 매핑이 표준화되어 있습니다. Nevertheless, certain SMSC have their own specific mapping: in this case, your **Adobe Campaign** administrator needs to declare this mapping. Check with your provider to find out more.

You can declare **data_codings** and force the encoding if necessary: to do this, specify a single encoding in the table.

* When no mapping of encodings is defined, the connector takes on a generic behavior:

   * It will try to use GSM encoding to which it assigns the value **data_coding = 0**.
   * If GSM encoding fails, it will use **UCS2** encoding to which it assigns the value **data_coding = 8**.

* 연결된 **[!UICONTROL data_coding]** 필드 값과 함께 사용할 인코딩을 정의하면 Adobe Campaign에서 목록의 첫 번째 인코딩을 사용하려고 시도합니다. 첫 번째 인코딩이 불가능하다고 입증되는 경우 다음을 수행합니다.

>[!IMPORTANT]
>
>선언의 순서는 중요합니다. 각 SMS 메시지 **에서 가능한 한 많은 문자를 입력할 수 있도록 인코딩에 맞게 목록을 비용** 오름차순으로 배치하는 것이 좋습니다.
>
>사용할 인코딩만 선언합니다. SMSC에서 제공하는 인코딩 중 일부가 사용 목적에 부합되지 않아야 하는 경우에는 목록에 선언하지 마십시오.

### 자동 회신 {#automatic-reply}

확장된 일반 SMPP 커넥터를 설정할 때 자동 응답을 구성할 수 있습니다.

구독자가 Adobe Campaign을 통해 전송한 SMS 메시지에 응답하고 해당 메시지에 &quot;STOP&quot;과 같은 키워드가 포함되어 있으면 **[!UICONTROL Automatic reply sent to the MO]** 섹션에서 자동으로 다시 전송되는 메시지를 구성할 수 있습니다.

>[!NOTE]
>
>키워드는 대/소문자를 구분하지 않습니다.

각 키워드에 대해 배달 전송에 주로 사용되는 숫자인 짧은 코드를 지정한 다음 가입자에게 전송할 메시지를 입력합니다.

동작을 자동 응답에 연결할 수도 있습니다. **[!UICONTROL Send to quarantine]** 또는 **[!UICONTROL Remove from quarantine]**. 예를 들어 수신자가 &quot;STOP&quot; 키워드를 전송하는 경우 구독 취소 확인을 자동으로 수신하여 격리하도록 전송됩니다.

![](assets/extended_smpp_reply.png)

동작을 자동 응답에 연결하면 해당 키워드를 **[!UICONTROL Remove from quarantine]** 보내는 수신자가 자동으로 격리되지 않습니다.

받는 사람은 **[!UICONTROL Non deliverables and addresses]** > **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** 메뉴를 통해 사용할 수 있는 표에 **[!UICONTROL Non deliverables Management]** 나열되어 있습니다.

* 짧은 코드가 무엇이든 동일한 응답을 보내려면 열을 **[!UICONTROL Short code]** 비워 두십시오.
* 키워드에 상관없이 동일한 응답을 보내려면 열을 **[!UICONTROL Keyword]** 비워 두십시오.
* 응답을 보내지 않고 작업을 수행하려면 열을 **[!UICONTROL Response]** 비워 두십시오. 예를 들어 &quot;STOP&quot; 이외의 메시지로 답글을 보낸 사용자를 격리하지 않아도 됩니다.

동일한 공급자 계정을 가진 확장 일반 SMPP 커넥터를 사용하는 여러 외부 계정이 있는 경우 다음 문제가 발생할 수 있습니다. 짧은 코드로 회신을 보낼 때 외부 계정 연결 시 수신될 수 있습니다. 따라서 전송된 자동 회신은 예상 메시지가 될 수 없습니다.
이를 방지하려면 사용 중인 공급자에 따라 다음 솔루션 중 하나를 적용합니다.

* 각 외부 계정에 대해 하나의 공급자 계정을 만듭니다.
* > 탭 **[!UICONTROL System type]** 과 필드를 **[!UICONTROL Mobile]** 사용하여 각 짧은 코드를 **[!UICONTROL Connection settings]** 구별합니다. 각 계정에 대해 다른 값을 제공자에게 요청합니다.

   ![](assets/extended_smpp_system-type.png)

확장 일반 SMPP 커넥터를 사용하여 외부 계정을 설정하는 단계는 SMPP 외부 계정 [만들기](../../delivery/using/sms-channel.md#creating-an-smpp-external-account) 섹션에 자세히 설명되어 있습니다.

### 배달 템플릿 변경 {#changing-the-delivery-template}

Adobe Campaign provides you with a template for delivering to mobiles. 이 템플릿은 노드에서 사용할 수 **[!UICONTROL Resources > Templates > Delivery templates]** 있습니다. For more on this, refer to the [About templates](../../delivery/using/about-templates.md) section.

SMS 채널을 통해 전달하려면 채널 커넥터를 참조하는 템플릿을 만들어야 합니다.

기본 배달 템플릿을 유지하려면 복제한 다음 구성하는 것이 좋습니다.

아래 예에서는 앞에서 활성화된 SMPP 계정을 통해 메시지를 전달하는 템플릿을 만듭니다. 이렇게 하려면:

1. 노드로 **[!UICONTROL Delivery templates]** 이동합니다.
1. 템플릿을 마우스 오른쪽 단추로 **[!UICONTROL Send to mobiles]** 클릭하고 선택합니다 **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. 템플릿의 레이블(예: SMPP( **모바일로 전송)을 변경합니다**.

   ![](assets/s_user_mobile_template_change_02.png)

1. **[!UICONTROL Properties]**&#x200B;을 클릭합니다.
1. 탭에서 **[!UICONTROL General]** 이전 단계에서 생성한 외부 계정에 해당하는 라우팅 모드를 선택합니다.

   ![](assets/s_user_mobile_template_change_03.png)

1. 템플릿 **[!UICONTROL Save]** 을 만들려면 을 클릭합니다.

   ![](assets/s_user_mobile_template_list.png)

You now have an external account and a delivery template that let you deliver via SMS.

## Creating a SMS delivery {#creating-a-sms-delivery}

### Selecting the delivery channel {#selecting-the-delivery-channel}

To create a new SMS delivery, follow the steps below:

>[!NOTE]
>
>Global concepts on delivery creation are presented in [this section](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Create a new delivery, for example from the Delivery dashboard.
1. Select the delivery template **Sent to mobiles (SMPP)** that you created earlier. For more on this, refer to the [Changing the delivery template](#changing-the-delivery-template) section.

   ![](assets/s_user_mobile_wizard.png)

1. Identify your delivery with a label, code, and description. 이 작업에 대한 자세한 정보는 [이 섹션](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery)을 참조하십시오.
1. Click **[!UICONTROL Continue]** to confirm this information and display the message configuration window.

## Defining the SMS content {#defining-the-sms-content}

SMS의 내용을 만들려면 아래 단계를 수행하십시오.

1. Enter the content of the message in the **[!UICONTROL Text content]** section of the wizard. 도구 모음 단추를 사용하여 내용을 가져오거나 저장 또는 검색할 수 있습니다. The last button is used to insert personalization fields.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   개인화 필드의 사용은 개인화 [정보 섹션에](../../delivery/using/about-personalization.md) 표시됩니다.

1. Click **[!UICONTROL Preview]** at the bottom of the page to view the rendering of the message with its personalization. To launch the preview, select a recipient using the **[!UICONTROL Test personalization]** button in the toolbar. You can select a recipient from the defined targets or choose another recipient.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   You can approve the SMS message. You can also view the content of the SMS on the mobile phone screen displayed on the right of the content editor. Click the screen and use the mouse to scroll through the content.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Click the **[!UICONTROL Data loaded]** link to view the information concerning the recipient.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >SMS messages are limited to a length of 160 characters if the Latin-1 (ISO-8859-1) code page is used. If the message is written in Unicode, it must not exceed 70 characters. Certain special characters can affect message length. For more information on message length, refer to the [About character transliteration](#about-character-transliteration) section.
   >
   >When personalization fields or conditional content fields are present, the size of the message varies from one recipient to the other. The length of the message must be evaluated when personalization has been carried out.
   >
   >When you launch the analysis, the length of messages is checked and a warning is displayed in the event of overflow.

1. NetSize 커넥터 또는 SMPP 커넥터를 사용하는 경우 배달 보낸 사람의 이름을 개인화할 수 있습니다. 자세한 내용은 [고급 매개 변수](#advanced-parameters) 섹션을 참조하십시오.

## 대상 모집단 선택 {#selecting-the-target-population}

게재의 대상 모집단을 선택할 때의 세부 프로세스는 [이 섹션에 나와 있습니다](../../delivery/using/steps-defining-the-target-population.md).

개인화 필드 사용에 대한 자세한 내용은 개인화 [정보를 참조하십시오](../../delivery/using/about-personalization.md).

시드 목록 포함에 대한 자세한 내용은 [시드 주소 정보를 참조하십시오](../../delivery/using/about-seed-addresses.md).

## SMS 메시지 전송 {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validating the delivery](../../delivery/using/steps-validating-the-delivery.md)
* [Sending the delivery](../../delivery/using/steps-sending-the-delivery.md)

### Advanced parameters {#advanced-parameters}

The **[!UICONTROL Properties]** button gives access to the advanced delivery parameter. The parameters specific to SMS deliveries are in the **[!UICONTROL SMS parameters]** section of the **[!UICONTROL Delivery]** tab.

다음 옵션을 사용할 수 있습니다.

* **Sender address**: lets you personalize the name of the delivery sender using a string of alphanumeric characters limited to eleven characters. The field must not be exclusively made up of figures. You can define a condition to display, for example, different names according to the area code of the recipient:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Check the law in your country regarding editing sender names. You should also check with your operator whether they offer this functionality.

* **Transmission mode**: message transmission by SMS.
* **우선 순위**: 메시지에 할당된 중요도 수준. **[!UICONTROL Normal]** priority is selected by default. Ask your service provider about the cost of SMS sent with **[!UICONTROL High]** priority.
* **Type of application**: choose the application you wish to assign to your SMS delivery. The **[!UICONTROL Direct Marketing]** option is selected by default and is the most common one used.

**Parameters specific to the NetSize connector**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Use several SMS for a single message**: this lets you send a message over 160 characters long via several SMS messages.

**Parameters specific to an SMPP connector**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Maximum number of SMS per message**: this option lets you set the number of SMS to use to send a message. If the number is set to 0, you can use an SMS to deliver your message. If the number of SMS is set to 1 or 2 for instance, and the message exceeds this threshold, it will not be sent.

## Monitoring and tracking SMS deliveries {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [게재 모니터링](../../delivery/using/monitoring-a-delivery.md)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [About message tracking](../../delivery/using/about-message-tracking.md)

## Processing inbound messages {#processing-inbound-messages}

nlserver sms **모듈은 SMS** 라우터를 정기적으로 쿼리합니다. 이를 통해 Adobe Campaign은 게재 진행 상황을 추적하고 상태 보고서와 수신자 구독 취소 요청을 처리할 수 있습니다.

* **상태 보고서**: 전달 로그를 확인하여 메시지 상태를 확인합니다.

   >[!NOTE]
   >
   >전송된 모든 SMS는 기본 키를 사용하는 외부 계정에 연결됩니다. 이 방법은 다음과 같습니다.
   >
   > * 삭제된 외부 SMS 계정의 상태 보고서가 올바르게 처리되지 않습니다.
   > * SMS 계정은 상태 보고서가 올바른 계정에 속하는지 확인하기 위해 단일 외부 계정에만 연결할 수 있습니다


* **구독 취소**: SMS 전달 수신을 중지하려는 수신자는 STOP이라는 단어가 포함된 메시지를 반환할 수 있습니다. 공급자가 계약 약관에 따라 메시지를 허용하는 경우 **인바운드 SMS** 워크플로우 활동을 통해 메시지를 검색한 다음 쿼리를 만들어 관련 받는 사람에게 **더 이상 이 수신자** 에게 연락하지 않음 옵션을 활성화할 수 있습니다.

   워크플로우 [가이드를](../../workflow/using/architecture.md) 참조하십시오.

## InSMS 스키마 {#insms-schema}

InSMS 스키마는 들어오는 SMS와 관련된 정보를 포함합니다. A description of these fields is available via the desc attribute.

* **메시지**: 수신한 SMS 컨텐츠
* **origin**: mobile number at the origin of message.
* **providerId**: SMSC(메시지 센터)가 반환하는 메시지의 식별자입니다.
* **created**: 수신 메시지 날짜가 Adobe Campaign에 삽입되었습니다.
* **extAccount**: Adobe Campaign 외부 계정.

   >[!IMPORTANT]
   >
   >The following fields are specific to NetSize.
   >
   >사용 중인 연산자가 NetSize가 아닌 경우 이러한 필드는 비어 있는 것으로 간주됩니다.

* **별칭**: 받는 메시지의 별칭입니다.
* **구분 기호**: 메시지의 별칭과 본문 사이의 구분자입니다.
* **messageDate**: 메시지 날짜.
* **receivalDate**: date message from operator was received by SMSC (message center).
* **deliveryDate**: date message sent by SMSC (message center).
* **largeAccount**: customer account code linked to incoming SMS.
* **countryCode**: operator country code.
* **operatorCode**: operator network code.
* **linkedSmsId**: 이 SMS가 응답인 나가는 SMS에 연결된 Adobe Campaign ID(broadlogId)입니다.

## Managing automatic replies (American regulation) {#managing-automatic-replies--american-regulation-}

구독자가 Adobe Campaign을 통해 전송된 SMS 메시지에 응답하고 STOP, HELP 또는 YES와 같은 키워드를 사용하는 경우 미국 시장에서 자동으로 반환되는 메시지를 구성해야 합니다.

For example, if recipients send the keyword STOP, they automatically receive a confirmation message stating that they have been unsubscribed.

이 유형의 메시지에 대한 보낸 사람 이름은 일반적으로 배달을 보내는 데 사용되는 짧은 코드입니다.

>[!IMPORTANT]
>
>The following detailed procedure is only valid for SMPP connectors, except for the extended generic SMPP connector. 자세한 내용은 SMPP [외부 계정](#creating-an-smpp-external-account) 만들기 섹션을 참조하십시오.
>
>미국의 마케팅 활동을 위해 미국 운영자들이 실시한 인증 과정의 일부를 담게 됩니다. These replies to subscriber SMS messages containing the keyword must be sent back to the subscriber immediately after receiving a message from them.

1. 다음 유형의 XML 파일을 만듭니다.

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. 태그의 **이름** 특성에 **`<shortcode>`** 대해 메시지 보낸 사람 이름 대신 표시할 짧은 코드를 지정합니다.

   각 **`<reply>`** 태그에 키워드와 함께 **키워드** 속성을 **입력하고** text특성과 함께 이 키워드에 보낼 메시지를 입력합니다.

   >[!NOTE]
   >
   >각 키워드는 대문자로 작성해야 합니다.

   여러 키워드에 대해 동일한 메시지를 보내려면 해당 줄을 복제합니다.

   예:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Once completed, save this file under the name **smsAutoReply.xml**.

   Note that the name of the file is case sensitive in Linux.

1. Copy this file into the **conf** directory in Adobe Campaign, at the same place as the Web server.

>[!IMPORTANT]
>
>These kinds of automatic messages do not keep a history. Therefore they do not appear in the [delivery dashboard](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).
>
>These messages are not considered part of the [commercial pressure rules](../../campaign/using/pressure-rules.md).
