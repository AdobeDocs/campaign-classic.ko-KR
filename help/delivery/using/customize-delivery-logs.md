---
product: campaign
title: 고급 - 게재 로그 사용자 지정
description: 게재 로그 스키마를 확장하여 Campaign Classic v7의 사용자 지정 필드를 추가하는 방법을 알아봅니다
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# 고급: 게재 로그 사용자 지정 {#customize-delivery-logs}

>[!NOTE]
>
>게재 목록 액세스 및 게재 대시보드 사용에 대한 포괄적인 지침은 [Campaign v8 설명서](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard)에 설명되어 있습니다. 이 콘텐츠는 Campaign Classic v7 및 Campaign v8 사용자 모두에게 적용됩니다.
>
>이 페이지는 하이브리드 및 온-프레미스 배포를 위한 **Campaign Classic v7별 고급 사용자 지정**&#x200B;을 문서화합니다.

Campaign UI에서 게재를 모니터링하려면 [Campaign v8 Campaign UI 설명서에서 게재 모니터링](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}을 참조하세요.

## 게재 로그 사용자 지정 {#use-case}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 스키마를 확장하여 게재 로그를 사용자 지정할 수 있습니다. 이 섹션에서는 게재 로그에 보낸 사람의 IP 주소를 추가하는 방법을 보여줍니다.

>[!NOTE]
>
>이 사용자 지정을 사용하려면 온-프레미스 배포에서 사용할 수 있는 스키마 확장 기능이 필요합니다. Campaign v8 Managed Cloud Services 사용자는 사용자 지정 게재 로그 필드가 필요하면 Adobe 고객 지원 센터에 문의해야 합니다.
>
>이 수정 사항은 단일 인스턴스 또는 중간 소싱 인스턴스를 사용하는 경우에 다릅니다. 수정하기 전에 이메일 전송 인스턴스에 연결되어 있는지 확인하십시오.

### 1단계: 스키마 확장

게재 로그에 **publicID**&#x200B;를 추가하려면 먼저 스키마를 확장해야 합니다. 다음과 같이 진행할 수 있습니다.

1. **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**&#x200B;에서 스키마 확장을 만듭니다.

   스키마 확장에 대한 자세한 내용은 [이 페이지](../../configuration/using/extending-a-schema.md)를 참조하세요.

1. **[!UICONTROL broadLogRcp]**&#x200B;을(를) 선택하여 NMS(받는 사람 게재 로그)를 확장하고 사용자 지정 네임스페이스를 정의합니다. 이 경우 &quot;cus&quot;가 됩니다.

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >인스턴스가 중간 소싱에 있는 경우 broadLogMid 스키마와 작업해야 합니다.

1. 확장에 새 필드를 추가합니다. 이 샘플에서는 다음을 교체해야 합니다.

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   수행한 사람:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### 2단계: 데이터베이스 구조 업데이트

수정이 완료되면 데이터베이스 구조가 논리적 설명과 일치하도록 업데이트해야 합니다.

이렇게 하려면 아래 단계를 수행합니다.

1. **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]** 메뉴를 클릭합니다.

   ![](assets/update-database-structure.png)

1. **[!UICONTROL Edit tables]** 창에서 아래와 같이 **[!UICONTROL NmsBroadLogRcp]** 테이블(또는 중간 소싱 환경에 있는 경우 **[!UICONTROL broadLogMid]** 테이블)을 확인합니다.

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >**[!UICONTROL NmsBroadLoGRcp]** 테이블(또는 중간 소싱 환경에 있는 경우 **[!UICONTROL broadLogMid]** 테이블)을 제외한 다른 수정 사항이 없는지 항상 확인하십시오. 이 경우 다른 테이블의 선택을 취소합니다.

1. 유효성을 검사하려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭하십시오. 다음 화면이 표시됩니다.

   ![](assets/update-script.png)

1. 데이터베이스 구조 업데이트를 시작하려면 **[!UICONTROL Next]**&#x200B;을(를) 클릭한 다음 **[!UICONTROL Start]**&#x200B;을(를) 클릭합니다. 색인 빌드를 시작하고 있습니다. 이 단계는 **[!UICONTROL NmsBroadLogRcp]** 테이블의 행 수에 따라 길어질 수 있습니다.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>데이터베이스의 물리적 구조 업데이트가 성공적으로 완료되면 수정 사항을 고려하도록 연결을 끊고 다시 연결해야 합니다.

### 3단계: 수정 사항 유효성 검사

모든 것이 올바르게 작동하는지 확인하려면 게재 로그 화면을 업데이트해야 합니다.

이렇게 하려면 게재 로그에 액세스하고 &quot;IP 식별자&quot; 열을 추가합니다.

![](assets/list-config.png)

>[!NOTE]
>
>Campaign Classic 인터페이스에서 목록을 구성하는 방법에 대해 알아보려면 [이 페이지](../../platform/using/adobe-campaign-workspace.md)를 참조하세요.

수정 후 **[!UICONTROL Delivery]** 탭에 표시되는 내용은 다음과 같습니다.

![](assets/logs-with-ip.png)

## 관련 항목

* [Campaign UI에서 게재 모니터링](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}(Campaign v8 설명서)
* [게재 상태](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"}(Campaign v8 설명서)
* [게재 실패 이해](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}(Campaign v8 설명서)
* [격리 관리](https://experienceleague.adobe.com/ko/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}(Campaign v8 설명서)
* [스키마 확장](../../configuration/using/extending-a-schema.md)(v7 하이브리드/온-프레미스)

