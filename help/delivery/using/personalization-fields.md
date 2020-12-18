---
solution: Campaign Classic
product: campaign
title: 개인화 필드
description: 개인화 필드
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 8%

---


# 개인화 필드{#personalization-fields}

개인화 필드는 게재된 메시지 콘텐츠의 첫 번째 수준 개인화에 사용됩니다. 주 콘텐츠에 삽입하는 필드는 선택한 데이터 소스의 데이터를 삽입할 위치를 보여줍니다.

예를 들어, **&lt;%= recipient.LastName %>** 구문을 사용하는 개인화 필드는 Adobe Campaign에 받는 사람의 이름을 데이터베이스(수신자 테이블)에 삽입하도록 지시합니다.

![](assets/do-not-localize/how-to-video.png) [비디오에서 이 기능 살펴보기](#personalization-fields-video)

>[!CAUTION]
>
>개인화 필드 내용은 1024자를 초과할 수 없습니다.

## 데이터 소스 {#data-sources}

선택한 전달 모드에 따라 개인화 필드는 두 가지 유형의 데이터 소스에서 가져올 수 있습니다.

* Adobe Campaign 데이터베이스는 데이터 소스입니다. &#39;수신자 개인화 필드&#39;와 같이 가장 일반적으로 사용됩니다. 표준 필드(일반적으로 다음과 같은 경우든 수신자 테이블에 정의된 모든 필드입니다.성, 이름, 주소, 마을, 생년월일 등) 또는 사용자 정의 필드를 선택합니다.
* 외부 파일은 데이터 소스입니다. 외부 파일에 있는 데이터를 사용하여 배달을 진행하는 동안 입력으로 표시된 파일의 열에 정의된 모든 필드입니다.

>[!NOTE]
>
>Adobe Campaign 개인화 태그의 형식은 항상 **&lt;%=table.field%>**&#x200B;입니다.

## 개인화 필드 삽입 {#inserting-a-personalization-field}

개인화 필드를 삽입하려면 머리글, 제목 또는 메시지 본문 편집 필드에서 액세스할 수 있는 드롭다운 아이콘을 클릭합니다.

![](assets/s_ncs_user_add_custom_field.png)

데이터 소스(수신자 필드 또는 파일 필드)를 선택한 후 이 삽입은 Adobe Campaign에서 해석하고 지정된 수신자의 필드 값으로 바뀌는 명령 형식을 취합니다. 그런 다음 물리적 교체를 **[!UICONTROL Preview]** 탭에서 볼 수 있습니다.

## 개인화 필드 예 {#personalization-fields-example}

먼저 받는 사람의 이름을 삽입한 다음 메시지 본문에 프로필 만들기 날짜를 추가하는 전자 메일을 만듭니다. 방법은 다음과 같습니다.

1. 새 배달을 만들거나 기존 이메일 유형 배달을 엽니다.
1. 배달 마법사에서 **[!UICONTROL Subject]**&#x200B;을 클릭하여 메시지 제목을 편집하고 제목을 입력합니다.
1. &quot; **[!UICONTROL Special offer for]**&quot;을 입력하고 도구 모음의 단추를 사용하여 개인화 필드를 삽입합니다. **[!UICONTROL Recipients>Title]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. 받는 사람의 이름을 삽입하려면 작업을 반복합니다. 모든 개인화 필드 사이에 공백을 삽입합니다.
1. 유효성을 확인하려면 **[!UICONTROL OK]**&#x200B;을 클릭합니다.
1. 메시지 본문에 개인화를 삽입합니다. 이렇게 하려면 메시지 내용을 클릭하고 필드 삽입 단추를 클릭합니다.
1. **[!UICONTROL Recipient>Other...]**&#x200B;을(를) 선택합니다.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. 표시할 정보가 있는 필드를 선택하고 **[!UICONTROL OK]**&#x200B;을 클릭합니다.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. 개인화 결과를 보려면 **[!UICONTROL Preview]** 탭을 클릭합니다. 받는 사람의 메시지를 표시하려면 받는 사람을 선택해야 합니다.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >배달을 워크플로우에 포함시키면 임시 워크플로우 테이블의 데이터를 사용할 수 있습니다. 이 데이터는 **[!UICONTROL Target extension]** 메뉴에서 그룹화됩니다. 이 작업에 대한 자세한 정보는 [이 섹션](../../workflow/using/data-life-cycle.md#target-data)을 참조하십시오.

## 개인화 최적화 {#optimizing-personalization}

전용 옵션을 사용하여 개인화를 최적화할 수 있습니다.**[!UICONTROL Prepare the personalization data with a workflow]**. 배달 속성의 **[!UICONTROL Analysis]** 탭에서 사용할 수 있습니다. 배달 분석에 대한 자세한 내용은 [이 섹션](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)을 참조하십시오.

배달 분석 중에 이 옵션은 FDA에 연결된 테이블의 데이터를 포함하여, 대상에 연결된 모든 데이터를 임시 테이블에 저장하는 워크플로우를 자동으로 만들고 실행합니다.

이 옵션을 선택하면 대량의 데이터가 처리되는 경우 특히 개인화 데이터가 FDA를 통해 외부 테이블에서 가져오는 경우 배달 분석 성능을 크게 향상시킬 수 있습니다. 자세한 내용은 [외부 데이터베이스 액세스(FDA)](../../installation/using/about-fda.md)를 참조하십시오.

예를 들어 메시지 컨텐츠에서 많은 개인화 필드 및/또는 개인화 블록을 사용하면서 수신자에게 전달할 때 성능 문제가 발생하는 경우, 이 옵션을 사용하면 개인화 처리 시간을 단축하여 메시지를 전달할 수 있습니다.

이 옵션을 사용하려면 아래 절차를 따르십시오.

1. 캠페인 만들기. 이 작업에 대한 자세한 정보는 [이 섹션](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)을 참조하십시오.
1. 캠페인의 **[!UICONTROL Targeting and workflows]** 탭에서 워크플로우에 **쿼리** 활동을 추가합니다. 이 활동 사용에 대한 자세한 내용은 [이 섹션](../../workflow/using/query.md)을 참조하십시오.
1. 워크플로우에 **[!UICONTROL Email delivery]** 활동을 추가하고 엽니다. 이 활동 사용에 대한 자세한 내용은 [이 섹션](../../workflow/using/delivery.md)을 참조하십시오.
1. **[!UICONTROL Delivery properties]**&#x200B;의 **[!UICONTROL Analysis]** 탭으로 이동하여 **[!UICONTROL Prepare the personalization data with a workflow]** 옵션을 선택합니다.

   ![](assets/perso_optimization.png)

1. 제공을 구성하고 분석을 시작할 워크플로우를 시작합니다.

분석이 완료되면 개인화 데이터는 분석 중에 생성되는 임시 기술 워크플로우를 통해 임시 테이블에 저장됩니다.

이 워크플로우는 Adobe Campaign 인터페이스에 표시되지 않습니다. 개인화 데이터를 신속하게 저장 및 처리하기 위한 기술적 방법일 뿐입니다.

분석이 완료되면 워크플로우 **[!UICONTROL Properties]**&#x200B;으로 이동하여 **[!UICONTROL Variables]** 탭을 선택합니다. 여기에서 SQL 호출을 수행하는 데 사용할 수 있는 임시 테이블의 이름을 볼 수 있으므로 SQL에 포함된 ID를 표시할 수 있습니다.

![](assets/perso_optimization_temp_table.png)

## 개인화 시간 초과 단계 {#timing-out-personalization}

전달 보호를 개선하기 위해 개인화 단계에 대해 제한 기간을 설정할 수 있습니다.

**[!UICONTROL Delivery properties]**&#x200B;의 **[!UICONTROL Delivery]** 탭에서 **[!UICONTROL Maximum personalization run time]** 옵션에 대한 최대 값(초)을 선택합니다.

미리 보거나 보내는 동안 개인화 단계가 이 필드에서 설정한 최대 시간을 초과하면 오류 메시지와 함께 프로세스가 중단되고 배달이 실패합니다.

![](assets/perso_time-out.png)

기본값은 5초입니다.

이 옵션을 0으로 설정하면 개인화 단계에 대해 시간 제한이 없습니다.

## 자습서 비디오 {#personalization-fields-video}

개인화 필드를 제목 줄 및 이메일 전달의 컨텐츠에 추가하는 방법을 알아봅니다.

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

추가 Campaign Classic 방법 비디오는 [여기](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=ko)에서 사용할 수 있습니다.
