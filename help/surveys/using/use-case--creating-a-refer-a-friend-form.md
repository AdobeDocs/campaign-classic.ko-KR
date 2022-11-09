---
product: campaign
title: 친구 설문 조사 참조 만들기
description: 친구 양식 참조 만들기 단계를 배웁니다.
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
source-git-commit: 1f80c9967f4859f26dd2890d657f95ada6cf2087
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---

# 활용 사례: 참조 양식 만들기{#use-case-creating-a-refer-a-friend-form}

![](../../assets/common.svg)

이 예제에서는 데이터베이스의 수신자에게 경쟁 제품을 제공하려고 합니다. 웹 양식에는 답변을 입력하는 섹션과 이메일 주소를 입력하여 친구를 참조하는 섹션이 있습니다.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

식별과 경쟁 블록은 이전에 설명한 프로세스를 사용하여 작성됩니다.

참조 블록을 구성하고 만들려면 다음 단계를 적용합니다.

1. 아래 그림과 같이 친구의 연락처 정보를 입력할 수 있는 페이지와 질문이 있는 경쟁 웹 양식을 만듭니다.

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   다음 **메시지** 필드를 사용하면 심판 메시지를 입력할 수 있습니다. 레퍼러도 레퍼러에 입력해야 합니다 **성**, **이름** 및 **이메일**.

   필드에 입력한 정보는 방문자 테이블이라는 특정 테이블에 저장됩니다.

   >[!NOTE]
   >
   >수신자가 동의하지 않는 한 수신자와 함께 데이터베이스에 저장할 수 없습니다. 이 파일은 일시적으로 **방문자** 테이블 (**nms:visitor**) 바이럴 마케팅 캠페인을 위해 설계되었습니다. 이 테이블은 **청소** 작업.
   >
   >이 예에서는 수신자를 타겟팅하여 레퍼러가 권장하는 경쟁에 참여하도록 유도하려고 합니다. 그러나 이 메시지에서는 그들에게 저희 정보 서비스 중 하나를 구독해 줄 수 있습니다. 구독하면 데이터베이스에 저장할 수 있습니다.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   심판과 관련된 필드의 콘텐츠는 프로필 만들기 스크립트와 심판에게 보내는 메시지에 사용됩니다.

1. 레퍼러를 심판에 연결하는 스크립트를 만들어 시작합니다.

   여기에는 다음 지침이 포함되어 있습니다.

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   페이지 식별 블록에 입력한 성, 이름 및 이메일 주소는 레퍼러의 성, 이름 및 이메일 주소로 식별됩니다. 이러한 필드는 심판에게 보내는 메시지 본문에 다시 삽입됩니다.

   APP5 값은 웹 양식의 내부 이름과 일치합니다. 이 정보를 사용하면 심판의 출처를 확인할 수 있습니다. 즉, 방문자를 만들어진 웹 양식에 연결할 수 있습니다.

1. 저장소 상자에서는 정보를 수집하여 데이터베이스에 저장할 수 있습니다.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. 그런 다음 1단계에서 만든 정보 서비스에 연결된 게재 템플릿을 만듭니다. 에서 선택됩니다 **[!UICONTROL Choose scenario]** 정보 서비스의 필드입니다.

   참조 오퍼 메시지를 만드는 데 사용되는 게재 템플릿에는 다음 정보가 포함됩니다.

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   이 템플릿에는 다음과 같은 특성이 있습니다.

   * 방문자 테이블을 대상 매핑으로 선택합니다.

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * 레퍼러에 대한 정보와 심판의 연락처 정보는 방문자 테이블에서 가져옵니다. 개인화 단추를 사용하여 삽입됩니다.

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * 이 템플릿에는 경기 양식 링크와 심판이 뉴스레터에 가입할 수 있는 구독 링크가 포함되어 있습니다.

      구독 링크는 개인화 블록을 통해 삽입됩니다. 기본적으로 프로필을 **뉴스레터** 서비스. 예를 들어 수신자를 다른 서비스에 가입시키는 등의 사용자의 필요에 따라 이 개인화 블록을 변경할 수 있습니다.

   * 내부 이름(&#39;referrer&#39; here)은 아래와 같이 메시지 전달 스크립트에서 사용됩니다.
   >[!NOTE]
   >
   >을(를) 참조하십시오. [이 페이지](../../delivery/using/about-templates.md) 게재 템플릿에 대한 자세한 내용은 를 참조하십시오.

1. 구독 메시지를 전달하는 두 번째 스크립트를 만듭니다.

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. 경쟁 양식을 게시하고 초기 타겟의 수신자에게 초대장을 보냅니다. 그들 중 한 사람이 친구를 초대하면, 게재를 기반으로 합니다 **참조 오퍼** 템플릿이 만들어집니다.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   심판은 의 방문자 폴더에 추가됩니다 **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   프로필에는 레퍼러가 입력한 정보가 포함되어 있습니다. 양식 스크립트에 입력된 구성을 기반으로 저장됩니다. 뉴스레터에 가입하기로 결정하면 수신자 표에 저장됩니다.
