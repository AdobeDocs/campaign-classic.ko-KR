---
product: campaign
title: 게재 상태
description: 게재 대시보드에서 사용할 수 있는 상태에 대해 자세히 알아보기
badge-v8: label="v8에도 적용됩니다." type="Positive" tooltip="Campaign v8에도 적용됩니다."
feature: Monitoring, Deliverability
role: User
exl-id: 0663257a-3a70-4e0c-bbeb-8242aaa0876d
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 2%

---

# 게재 상태 {#delivery-statuses}



<!--ajouter intro 

ajouter screenshot -->

게재가 전송되면 게재 대시보드에 전송 성공 여부를 모니터링할 수 있는 상태가 표시됩니다. 가능한 상태는 아래 섹션에 자세히 설명되어 있습니다.

![](assets/delivery-status.png)

발생할 수 있는 다양한 게재 실패와 해결 방법에 대한 자세한 내용은 [이 페이지](understanding-delivery-failures.md)를 참조하세요.

**관련 항목:**

* [게재 대시보드](delivery-dashboard.md)
* [게재 문제 해결](delivery-troubleshooting.md)
* [게재 기능 시작](about-deliverability.md)

## 게재 상태 목록 {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> 상태<br /> </th> 
   <th> 정의 및 솔루션<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 보냄<br /> </td> 
   <td> 게재가 메시지 공급자에게 올바르게 전송되었지만 받는 사람이 받을 필요는 없습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 무시됨<br /> </td> 
   <td> 주소 오류로 인해 수신자에게 게재가 전송되지 않았습니다. 차단 목록, 격리, 제공되지 않거나 중복되었습니다. <br /> </td> 
  </tr> 
  <tr> 
   <td> 실패<br /> </td> 
   <td> 잘못된 주소 또는 전체 받은 편지함 등으로 인해 게재가 수신자에게 도달하지 못했습니다. 또한 스키마가 게재 매핑과 일치하지 않을 때 오류를 생성할 수 있으므로 개인화 블록의 문제와 연결할 수도 있습니다. <a href="understanding-delivery-failures.md" target="_blank">게재 오류 이해</a><br />를 참조하세요. </td> 
  </tr>
  <tr> 
   <td> 보류 중<br /> </td> 
   <td> 게재를 보낼 준비가 되었으며 게재 서버(MTA)에서 처리합니다. <a href="#pending-status" target="_blank">보류 중 상태</a>.<br /> 보기 </td> 
  </tr> 
  <tr> 
   <td> 적용할 수 없음<br /> </td> 
   <td> 서버(MTA)에서 게재를 고려했지만 처리되지 않았습니다.<br /> </td> 
  </tr>  
  <tr> 
   <td> 게재 취소됨<br /> </td> 
   <td> 연산자가 게재를 취소했습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 서비스 공급자가 고려함<br /> </td> 
   <td> SMS 서비스 공급자가 게재를 받았습니다.<br /> 호스팅 또는 하이브리드 설치의 경우 <a href="sending-with-enhanced-mta.md" target="_blank">Enhanced MTA</a>(으)로 업그레이드한 경우 메시지가 Campaign에서 Enhanced MTA로 성공적으로 릴레이되었습니다.</td> 
  </tr> 
  <tr> 
   <td> 모바일에서 수신됨<br /> </td> 
   <td> 받는 사람이 모바일 장치에서 SMS를 받았습니다.<br /> </td> 
  </tr>
  <tr> 
   <td> 서비스 공급자<br />에게 전송됨 </td> 
   <td> 게재를 SMS 서비스 공급자에게 보냈지만 아직 받지 못했습니다.<br />
   </td> 
  </tr> 
  <tr> 
   <td> 준비됨<br /> </td> 
   <td> 모바일 채널과 같은 외부 커넥터에만 사용되는 중개 상태. '보류 중' 상태를 따르며 다음 상태를 결정하는 외부 커넥터입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Adobe Campaign 이메일의 전달성을 최적화하는 방법에 대해 알아보려면 [이 섹션](about-deliverability.md)을 참조하세요. 전달성에 대한 자세한 내용은 [Adobe 전달성 모범 사례 안내서](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=ko)를 참조하세요.

## 보류 중인 상태 {#pending-status}

게재를 확인한 후 게재 상태가 **[!UICONTROL Pending]**&#x200B;임을 확인할 수 있습니다. 이 상태는 실행 프로세스가 일부 리소스의 가용성을 대기 중임을 의미합니다.

**[!UICONTROL Pending]** 상태는 먼저 게재가 예약되어 지정된 날짜까지 보류 중임을 의미할 수 있습니다. 자세한 내용은 [Campaign v8 설명서](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/configure-and-send.html?lang=ko#schedule-delivery-sending){target="_blank"}를 참조하세요.

게재를 보낼 수 없고 상태가 **[!UICONTROL Pending]**&#x200B;인 경우 다음 결과가 발생할 수 있습니다.

* 게재 서버에서 모듈 및 프로세스를 실행하고 이메일 전송을 관리하는 MTA(메시지 전송 에이전트)가 시작되지 않았거나 다시 시작해야 할 수 있습니다.

  이를 확인하고 필요한 경우 모듈을 시작하려면 다음 단계를 적용합니다.

  >[!NOTE]
  >
  >이 작업은 Campaign 서버에 액세스할 수 있는 **온-프레미스** 또는 **하이브리드** 호스팅 모델로 수행할 수 있습니다([호스팅 모델](../../installation/using/hosting-models.md) 참조).

   1. `mta@<instance>` 모듈이 MTA 서버에서 시작되었는지 확인합니다.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<instance-name> (9268) - 23.0 Mb
      [...]
      ```

   1. MTA가 나열되지 않으면 다음 명령으로 시작하십시오.

      ```
      nlserver start mta@<instance-name>
      ```

      >[!NOTE]
      >
      >`<instance-name>`을(를) 인스턴스 이름(프로덕션, 개발 등)으로 바꿉니다. 구성 파일을 통해 인스턴스 이름을 식별합니다. `[path of application]nl6/conf/config-<instance-name>.xml`

* 게재는 전송 서버에 구성되지 않은 선호도를 사용할 수 있습니다.

  이 경우 트래픽 관리(IP 선호도)의 구성을 확인하고 **[!UICONTROL Managing affinities with IP addresses]** 필드를 사용하여 선호도를 관리하는 MTA에 게재를 연결합니다. 관심도에 대한 자세한 내용은 [이 섹션](../../installation/using/configure-delivery-settings.md)을 참조하세요.

* 너무 많은 캠페인이 실행 중일 때 게재 상태는 &#39;보류 중&#39; 상태로 유지됩니다.

  동시 캠페인의 제한은 **[!UICONTROL NmsOperation_LimitConcurrency]** 옵션에 정의되어 있습니다. 기본값은 10입니다.

  [이 페이지](../../installation/using/configuring-campaign-options.md)의 옵션에 대해 자세히 알아보세요.


**관련 항목:**

* [게재 로그 및 내역](#delivery-logs-and-history)
* [게재 실패 이해](understanding-delivery-failures.md)
* [게재 실패 유형 및 이유](understanding-delivery-failures.md#delivery-failure-types-and-reasons)
