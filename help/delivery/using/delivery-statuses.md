---
solution: Campaign Classic
product: campaign
title: 배달 상태
description: 배달 대시보드에서 사용할 수 있는 상태에 대해 자세히 알아보십시오.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: de0e4555d3e2c5dff8d86a22ff4db85953105db1
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 3%

---


# 배달 상태 {#delivery-statuses}

<!--ajouter intro 

ajouter screenshot -->

배달을 전송하면 전송 대시보드에 전송이 성공했는지 여부를 모니터링할 수 있는 상태가 표시됩니다. 가능한 상태는 아래 섹션에 자세히 설명되어 있습니다.

![](assets/delivery-status.png)

발생할 수 있는 여러 가지 배달 실패와 그 해결 방법에 대한 자세한 내용은 [이 페이지](../../delivery/using/understanding-delivery-failures.md)를 참조하십시오.

**관련 항목:**

* [배달 대시보드](../../delivery/using/delivery-dashboard.md)
* [배달 문제 해결](../../delivery/using/delivery-troubleshooting.md)
* [게재 기능 기본 정보](../../delivery/using/about-deliverability.md)

## 배달 상태 목록 {#list-delivery-statuses}

<table> 
 <thead> 
  <tr> 
   <th> 상태<br /> </th> 
   <th> 정의 및 솔루션<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 보낸 날짜<br /> </td> 
   <td> 배달이 메시지 공급자에게 올바르게 전송되었지만 받는 사람이 메시지를 받을 필요가 없습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 무시됨<br /> </td> 
   <td> 주소가 잘못되어 배달이 받는 사람에게 전송되지 않았습니다. 이것은차단 목록에 있거나 격리되었으며, 제공되지 않았거나 복제되었습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 실패<br /> </td> 
   <td> 잘못된 주소 또는 전체 받은 편지함으로 인해 배달이 받는 사람에게 도달할 수 없습니다. 스키마가 배달 매핑과 일치하지 않을 때 오류를 생성할 수 있으므로 개인화 블록과 관련된 문제에 연결할 수도 있습니다. <a href="../../delivery/using/understanding-delivery-failures.md" target="_blank">배달 실패 이해</a><br />를 참조하십시오. </td> 
  </tr>
  <tr> 
   <td> 보류 중<br /> </td> 
   <td> 배달이 전송될 준비가 되었으며 배달 서버(MTA)에서 처리할 예정입니다. <a href="#pending-status" target="_blank">보류 중인 상태</a>를 참조하십시오.<br /> </td> 
  </tr> 
  <tr> 
   <td> 해당 없음<br /> </td> 
   <td> 배달은 서버(MTA)에서 고려했지만 처리되지 않았습니다.<br /> </td> 
  </tr>  
  <tr> 
   <td> 배달이 취소됨<br /> </td> 
   <td> 연산자가 배달을 취소했습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 서비스 공급자가 고려합니다<br />. </td> 
   <td> SMS 서비스 공급자가 배달을 받았습니다.<br /> </td> 
  </tr> 
  <tr> 
   <td> 모바일<br />에서 수신됨 </td> 
   <td> 수신자가 모바일 장치에서 SMS를 받았습니다.<br /> </td> 
  </tr>
  <tr> 
   <td> 서비스 공급자<br />(으)로 전송됨 </td> 
   <td> 배달이 SMS 서비스 공급자에게 전송되었지만 아직 수신되지 않았습니다.<br />
   </td> 
  </tr> 
  <tr> 
   <td> 준비됨<br /> </td> 
   <td> 모바일 채널과 같은 외부 커넥터에만 사용되는 중간 상태입니다. '보류 중' 상태를 따르고 다음 상태를 결정하는 외부 커넥터입니다.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Adobe Campaign 이메일의 전달 가능성을 최적화하는 방법에 대한 자세한 내용은 Adobe Campaign [전달 가능성 우수 사례 가이드](../../delivery/using/deliverability-key-points.md) 및 [이 페이지](../../delivery/using/about-deliverability.md)를 참조하십시오.

## 보류 중인 상태 {#pending-status}

배달을 확인한 후 배달 상태가 **[!UICONTROL Pending]**&#x200B;임을 확인할 수 있습니다. 이 상태는 실행 프로세스가 일부 리소스의 가용성을 기다리고 있음을 의미합니다.

**[!UICONTROL Pending]** 상태는 먼저 배달을 예약했으며 주어진 날짜까지 보류 중임을 의미합니다. 자세한 내용은 [배달 예약](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) 섹션을 참조하십시오.

배달이 전송되지 않고 해당 상태가 **[!UICONTROL Pending]**&#x200B;으로 남아 있는 경우 다음 결과의 결과일 수 있습니다.

* 배달 서버에서 모듈 및 프로세스를 실행하고 이메일 전송을 관리하는 MTA(메시지 전송 에이전트)가 시작되지 않았거나 다시 시작해야 할 수 있습니다.

   이 내용을 확인하고 필요한 경우 모듈을 시작하려면 다음 단계를 수행하십시오.

   >[!NOTE]
   >
   >이 작업은 캠페인 서버에 액세스할 수 있는 **온-프레미스** 또는 **하이브리드** 호스팅 모델을 사용하여 수행할 수 있습니다([호스팅 모델](../../installation/using/hosting-models.md) 참조).

   1. `mta@<instance>` 모듈이 MTA 서버에서 시작되었는지 확인합니다.

      ```
      nlserver pdump
      HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
      [...]
      mta@<INSTANCENAME> (9268) - 23.0 Mb
      [...]
      ```

   1. MTA가 목록에 없으면 다음 명령으로 시작합니다.

      ```
      nlserver start mta@<INSTANCENAME>
      ```

      >[!NOTE]
      >
      >`<INSTANCENAME>`을(를) 인스턴스 이름(프로덕션, 개발 등)으로 바꿉니다. 인스턴스 이름은 구성 파일을 통해 식별됩니다.`[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 배달은 전송 서버에서 구성되지 않은 선호도를 사용하고 있을 수 있습니다.

   이 경우 트래픽 관리(IP 친화성)의 구성을 확인하고 **[!UICONTROL Managing affinities with IP addresses]** 필드를 사용하여 친화성을 관리하는 MTA에 제공을 연결합니다. 친화성에 대한 자세한 내용은 [이 섹션](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)을 참조하십시오.

* 실행 중인 캠페인이 너무 많으면 배달 상태가 &#39;보류 중&#39; 상태로 유지됩니다.

   동시 캠페인의 제한은 **[!UICONTROL NmsOperation_LimitConcurrency]** 옵션에 정의됩니다. 기본값은 10입니다.

   [이 페이지](../../installation/using/configuring-campaign-options.md)의 옵션에 대해 자세히 알아보십시오.


**관련 항목:**

* [배달 로그 및 내역](#delivery-logs-and-history)
* [게재 실패 이해](../../delivery/using/understanding-delivery-failures.md)
* [게재 실패 유형 및 이유](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)
