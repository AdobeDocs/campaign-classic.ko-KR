---
product: campaign
title: 게재 템플릿 사용
description: 게재 템플릿 사용
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Delivery Templates
exl-id: a5da3f29-5eab-428c-b7c3-d9e4243fe628
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# 템플릿 사용 {#use-templates}



게재 템플릿은 가장 일반적인 유형의 활동에 대해 준비된 시나리오를 제공하여 효율성을 높입니다. 마케터는 템플릿을 사용하여 짧은 시간 내에 최소한의 사용자 지정으로 새 캠페인을 배포할 수 있습니다.

에서 게재 템플릿에 대해 자세히 알아보기 [이 섹션](creating-a-delivery-template.md).

## 게재 템플릿 시작 {#gs-templates}

A [게재 템플릿](creating-a-delivery-template.md) 을(를) 사용하면 사용자의 요구 사항에 맞고 향후 게재에 재사용할 수 있는 기술 및 기능 속성 세트를 한 번 정의할 수 있습니다. 그런 다음 시간을 절약하고 필요한 경우 게재를 표준화할 수 있습니다.

Adobe Campaign에서 여러 브랜드를 관리할 때, Adobe은 브랜드당 하나의 하위 도메인을 사용하는 것을 권장합니다. 예를 들어 은행은 각 지역 기관에 해당하는 여러 하위 도메인을 가질 수 있습니다. 은행이 bluebank.com 도메인을 소유하는 경우 해당 하위 도메인은 @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com 등이 될 수 있습니다. 하위 도메인당 하나의 게재 템플릿을 사용하면 각 브랜드에 대해 항상 올바른 사전 구성된 매개 변수를 사용할 수 있으므로 오류를 방지하고 시간을 절약할 수 있습니다.

**팁**: 구성 오류를 방지하려면 새 템플릿을 만드는 것보다 기본 템플릿을 복제하고 해당 속성을 변경하는 것이 좋습니다.

## 주소 구성

* 이메일을 보낼 수 있도록 하려면 발신자 주소가 필수입니다.

* 일부 ISP(인터넷 서비스 공급자)는 메시지를 수락하기 전에 보낸 사람 주소의 유효성을 확인합니다.

* 잘못된 형식의 주소는 수신 서버에서 거부될 수 있습니다. 주소가 정확한지 확인해야 합니다.

* 주소는 발신자를 명시적으로 식별해야 합니다. 도메인은 발신자가 소유하고 등록해야 합니다.

* Adobe은 게재 및 회신에 대해 지정된 주소에 해당하는 이메일 계정을 만들 것을 권장합니다. 메시징 시스템 관리자에게 문의하십시오.

Campaign 인터페이스에서 주소를 구성하려면 아래 단계를 따르십시오.

1. 다음에서 [게재 템플릿](creating-a-delivery-template.md)를 클릭하고 **[!UICONTROL From]** 링크를 클릭합니다. 다음에서 **[!UICONTROL Email header parameters]** 창에서 다음 필드를 입력합니다.

   ![](assets/d_best_practices_email_header.png)

1. 다음에서 **[!UICONTROL Sender address]** 필드에서 주소 도메인이 Adobe에게 위임한 하위 도메인과 동일한지 확인합니다. &#39;@&#39; 앞 부분은 변경할 수 있지만 도메인 주소는 변경할 수 없습니다.

1. 다음에서 **[!UICONTROL From]** 필드에서는 브랜드 이름과 같이 수신자가 쉽게 식별할 수 있는 이름을 사용하여 게재의 열람률을 높입니다. 수신자의 경험을 더 개선하기 위해 개인 이름을 추가할 수 있습니다(예: &quot;Megastore의 Emma&quot;).

1. 다음에서 **[!UICONTROL Reply address text]** 필드에서는 기본적으로 발신자의 주소가 회신에 사용됩니다. 그러나 Adobe은 브랜드의 고객 지원 센터와 같은 기존 실제 주소를 사용하는 것을 권장합니다. 이 경우 수신자가 회신을 보내면 고객 지원 센터에서 이를 처리할 수 있습니다.

### 컨트롤 그룹 설정

게재가 전송되면 제외된 수신자의 행동을 게재를 받은 수신자와 비교할 수 있습니다. 그런 다음 캠페인의 효율성을 측정할 수 있습니다. 컨트롤 그룹에 대해 자세히 알아보기 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

컨트롤 그룹을 설정하려면 **[!UICONTROL To]** 링크를 클릭합니다. 다음에서 **[!UICONTROL Select target]** 창에서 **[!UICONTROL Control group]** 탭. 대상의 일부, 예를 들어 5% 무작위 샘플을 추출할 수 있다.

![](assets/d_best_practices_control_group.png)

## 유형화를 사용하여 필터 또는 제어 규칙 적용

유형화에는 메시지를 보내기 전에 분석 단계 중에 적용되는 확인 규칙이 포함되어 있습니다.

다음에서 **[!UICONTROL Typology]** 템플릿 속성의 탭에서 필요에 따라 기본 유형화를 변경합니다.

예를 들어 아웃바운드 트래픽을 더 잘 제어하기 위해 하위 도메인당 하나의 선호도를 정의하고 선호도당 하나의 유형화를 만들어 사용할 수 있는 IP 주소를 정의할 수 있습니다. 관심도는 인스턴스의 구성 파일에 정의됩니다. Adobe Campaign 관리자에게 문의하십시오.

유형화에 대한 자세한 내용은 [이 섹션](../../campaign-opt/using/about-campaign-typologies.md).
