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



게재 템플릿을 사용하면 대부분의 일반적인 활동 유형에 대해 준비된 시나리오를 제공하여 효율성을 높일 수 있습니다. 마케터는 템플릿을 사용하여 짧은 시간에 최소한의 사용자 지정으로 새 캠페인을 배포할 수 있습니다.

에서 게재 템플릿에 대해 자세히 알아봅니다. [이 섹션](creating-a-delivery-template.md).

## 게재 템플릿 시작 {#gs-templates}

A [게재 템플릿](creating-a-delivery-template.md) 을(를) 통해 사용자의 요구 사항에 맞게 그리고 향후 게재에 재사용할 수 있는 기술 및 기능 속성 세트를 한 번 정의할 수 있습니다. 그런 다음 시간을 절약하고 필요한 경우 게재를 표준화할 수 있습니다.

Adobe Campaign에서 여러 브랜드를 관리하는 경우, 브랜드당 하나의 하위 도메인이 있는 것이 좋습니다. 예를 들어 은행은 각 지역 기관에 해당하는 여러 하위 도메인을 가질 수 있습니다. 블루뱅크 도메인은 은행@ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com 등이 될 수 있습니다. 하위 도메인당 하나의 게재 템플릿을 사용하면 각 브랜드에 대해 항상 올바른 사전 구성된 매개 변수를 사용할 수 있으므로 오류를 방지하고 시간을 절약할 수 있습니다.

**팁**: 구성 오류를 방지하려면 새 템플릿을 만들지 않고 기본 템플릿을 복제하고 해당 속성을 변경하는 것이 좋습니다.

## 주소 구성

* 이메일을 전송하도록 허용하려면 보낸 사람의 주소가 필수입니다.

* 일부 ISP(Internet Service Providers)는 메시지를 수락하기 전에 보낸 사람 주소의 유효성을 검사합니다.

* 잘못 형성된 주소는 수신 서버에서 거부될 수 있습니다. 올바른 주소가 지정되었는지 확인해야 합니다.

* 주소는 발신자를 명시적으로 식별해야 합니다. 도메인은 자신이 소유하고 발신자에게 등록해야 합니다.

* Adobe은 게재 및 답글에 지정된 주소에 해당하는 이메일 계정을 만드는 것을 권장합니다. 메시징 시스템 관리자에게 문의하십시오.

Campaign 인터페이스에서 주소를 구성하려면 아래 단계를 수행하십시오.

1. 에서 [게재 템플릿](creating-a-delivery-template.md)를 클릭하고 **[!UICONTROL From]** 링크를 클릭합니다. 에서 **[!UICONTROL Email header parameters]** 창에서 다음 필드를 입력합니다.

   ![](assets/d_best_practices_email_header.png)

1. 에서 **[!UICONTROL Sender address]** 필드에서 주소 도메인이 Adobe에 위임한 하위 도메인과 같은지 확인합니다. &#39;@&#39; 앞의 부분을 변경할 수 있지만 도메인 주소는 변경할 수 없습니다.

1. 에서 **[!UICONTROL From]** 필드에서 브랜드 이름과 같이 수신자가 쉽게 식별할 수 있는 이름을 사용하여 게재의 열기 비율을 높입니다. 수신자의 경험을 더 향상시키기 위해 &quot;Emma from Megastore&quot;와 같은 개인 이름을 추가할 수 있습니다.

1. 에서 **[!UICONTROL Reply address text]** 필드에서는 기본적으로 답글에 발신자의 주소가 사용됩니다. 하지만 Adobe은 브랜드의 고객 지원 센터에서 기존의 실제 주소와 같은 을 사용하는 것을 권장합니다. 이 경우 수신자가 답글을 보내면 고객 지원 센터에서 이를 처리할 수 있습니다.

### 컨트롤 그룹 설정

게재를 전송하면 제외된 수신자의 동작을 게재를 받은 수신자와 비교할 수 있습니다. 그런 다음 캠페인의 효율성을 측정할 수 있습니다. 컨트롤 그룹에 대해 자세히 알아보기 [이 섹션](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

컨트롤 그룹을 설정하려면 **[!UICONTROL To]** 링크를 클릭합니다. 에서 **[!UICONTROL Select target]** 창에서 **[!UICONTROL Control group]** 탭. 대상의 일부를 추출할 수 있습니다(예: 5% 임의 샘플).

![](assets/d_best_practices_control_group.png)

## 유형화를 사용하여 필터 또는 제어 규칙을 적용합니다

유형화에는 메시지를 보내기 전에 분석 단계 동안 적용되는 확인 규칙이 포함됩니다.

에서 **[!UICONTROL Typology]** 템플릿 속성의 탭에서 필요에 따라 기본 유형화를 변경합니다.

예를 들어 아웃바운드 트래픽을 더 잘 제어하기 위해 하위 도메인당 하나의 친화성을 정의하고 친화성당 하나의 유형화를 만들어 사용할 수 있는 IP 주소를 정의할 수 있습니다. 인스턴스의 구성 파일에 관심도가 정의됩니다. Adobe Campaign 관리자에게 문의하십시오.

유형화에 대한 자세한 내용은 [이 섹션](../../campaign-opt/using/about-campaign-typologies.md).
