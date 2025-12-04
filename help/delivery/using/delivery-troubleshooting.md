---
product: campaign
title: 게재 전송 문제 해결
description: 게재 성능 및 게재 모니터링과 관련된 문제를 해결하는 방법에 대해 자세히 알아보기
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: eac670cd4e7371ca386cee5f1735dc201bf5410a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# 게재 전송 문제 해결 {#delivery-troubleshooting}

>[!NOTE]
>
>게재 문제 해결에 대한 포괄적인 지침은 Campaign Classic v7 및 Campaign v8 사용자 모두에게 해당되는 Campaign v8 설명서에 기재되어 있습니다.
>
>* 일반적인 배달 오류 및 솔루션: [배달 오류 이해](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}
>* 느린 게재 진단: [Campaign UI에서 게재 모니터링](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}
>* 게재 모범 사례: [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}
>
>이 페이지에서는 하이브리드 및 온-프레미스 배포에 대한 **Campaign Classic v7 관련 문제 해결**&#x200B;에 대해 설명합니다.

## 문제 해결 {#v7-specific}

**Campaign Classic v7 하이브리드/온-프레미스 배포**&#x200B;의 경우 다음 문제 해결 단계는 관리하는 인프라에만 해당됩니다.

### MX 규칙 구성

특정 ISP에서 전송률 조절 문제가 발생하는 경우 MX 규칙 구성을 검토하고 조정해야 할 수 있습니다. MX 규칙 및 할당량에 대한 자세한 내용은 [이 섹션](../../installation/using/email-deliverability.md#about-mx-rules)을 참조하세요.

### 게재 성능을 위한 데이터베이스 유지 관리

중간 소싱 배포에서 다음 오류가 발생하는 경우:

```
Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
```

그 원인은 마케팅 인스턴스가 데이터를 중간 소싱 서버에 보내기 전에 데이터를 작성하는 데 너무 많은 시간을 소비하는 성능 문제와 관련되어 있습니다.

**온-프레미스 설치의 경우**&#x200B;데이터베이스에 대해 진공을 수행하고 다시 인덱싱합니다. 데이터베이스 유지 관리에 대한 자세한 내용은 [이 섹션](../../production/using/recommendations.md)을 참조하세요.

또한 예약된 활동이 있는 모든 워크플로우와 실패 상태에 있는 모든 워크플로우를 다시 시작해야 합니다. [이 섹션](../../workflow/using/scheduler.md)을 참조하십시오.

### 기술 워크플로우 모니터링

온-프레미스 설치의 경우 게재 가능성과 관련된 모든 기술 워크플로우가 오류 없이 실행되고 있는지 확인합니다.

**게재 기능 업데이트 워크플로**: 바운스 메일 자격 규칙 및 게재 기능 지표를 업데이트합니다.

**추적 워크플로**: 보낸 게재에 대한 추적 데이터를 처리합니다.

**데이터베이스 정리 워크플로우**: 성능을 유지하기 위해 이전 게재 로그와 임시 테이블을 정기적으로 제거합니다.

**[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**&#x200B;에서 워크플로 상태를 확인하십시오.

>[!NOTE]
>
>Campaign v8 Managed Cloud Services 사용자의 경우 기술 워크플로우 및 인프라 모니터링은 Adobe에서 관리합니다. [Campaign v8 설명서](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}에 설명된 대로 게재 콘텐츠 및 타깃팅에 집중하십시오.

## 관련 항목

* [게재 실패 이해](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}(Campaign v8 설명서)
* [게재 모범 사례](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/start/delivery-best-practices){target="_blank"}(Campaign v8 설명서)
* [Campaign UI에서 게재 모니터링](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}(Campaign v8 설명서)
* [데이터베이스 유지 관리](../../production/using/recommendations.md)(v7 하이브리드/온-프레미스)
* [이메일 전달성](../../installation/using/email-deliverability.md)(v7 하이브리드/온-프레미스)
