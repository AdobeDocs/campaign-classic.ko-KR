---
title: '"사용 사례:친구 양식 참조"'
seo-title: '"사용 사례:친구 양식 참조"'
description: '"사용 사례:친구 양식 참조"'
seo-description: null
page-status-flag: never-activated
uuid: ad8b9076-c551-420d-bb23-0b3c645ee943
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: bbb1154f-2818-489c-9860-0e860596cbf7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 사용 사례:친구 양식 참조{#use-case-creating-a-refer-a-friend-form}

이 예에서는 데이터베이스의 수신자에게 경쟁업체를 제공하려고 합니다. 웹 양식에는 답변을 입력하는 섹션과 이메일 주소를 입력하여 친구를 참조하는 섹션이 있습니다.

![](assets/s_ncs_admin_survey_viral_sample_0.png)

식별 및 경쟁 블록은 앞에서 설명한 프로세스를 사용하여 만들어집니다.

참조 블록을 구성하고 만들려면 다음 단계를 적용합니다.

1. 다음과 같이 질문 및 친구의 연락처 정보 입력 필드가 포함된 대회 웹 양식을 만듭니다.

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   메시지 **필드를** 사용하면 심판에 대한 메시지를 입력할 수 있습니다. 레퍼러는 성 **, 이름**&#x200B;및 이메일을 **입력해야** 합니다 ****.

   필드에 입력된 정보는 방문자 테이블이라는 특정 테이블에 저장됩니다.

   >[!NOTE]
   >
   >수신자가 동의하지 않은 경우 수신자와 함께 데이터베이스에 저장할 수 없습니다. 바이럴 마케팅 캠페인을 위해 설계된 **방문자** 테이블(**nms:visitor**)에 일시적으로 저장됩니다. 이 테이블은 **청소** 작업 덕분에 정기적으로 삭제됩니다.
   >
   >이 예에서는 수신자가 레퍼러가 추천하는 경쟁에 참가하도록 타깃팅하고자 합니다. 그러나 이 메시지에서는 Adobe 정보 서비스 중 하나에 대한 구독을 제공할 수 있습니다. 구독하면 데이터베이스에 저장할 수 있습니다.

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   심판과 관련된 필드의 내용은 프로필 작성 스크립트와 그들에게 전송된 메시지에서 사용됩니다.

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

   페이지 ID 블록에 입력된 성, 이름 및 이메일 주소는 레퍼러의 성, 이름 및 이메일 주소로 식별됩니다. 이러한 필드는 심판에게 보낸 메시지의 본문에 다시 주입될 것입니다.

   APP5 값은 웹 양식의 내부 이름과 일치합니다.이 정보를 통해 심판의 출처를 확인할 수 있습니다. 즉, 방문자를 만들어진 웹 양식과 연결할 수 있습니다.

1. 저장소 상자를 사용하면 정보를 수집하고 데이터베이스에 저장할 수 있습니다.

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. 그런 다음 1단계 동안 생성된 정보 서비스에 연결된 배달 템플릿을 만듭니다. 정보 서비스 **[!UICONTROL Choose scenario]** 필드에서 선택됩니다.

   참조 오퍼 메시지를 만드는 데 사용되는 배달 템플릿에는 다음 정보가 포함되어 있습니다.

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   이 템플릿에는 다음과 같은 특성이 있습니다.

   * 방문자 테이블을 대상 매핑으로 선택합니다.

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * 레퍼러의 정보는 물론 심판의 연락처 정보도 방문자 테이블에서 가져옵니다. 개인화 단추를 사용하여 삽입됩니다.

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * 이 템플릿에는 대회 양식과 심판의 뉴스레터 구독 링크가 포함되어 있습니다.

      구독 링크는 개인화 블록을 통해 삽입됩니다. 기본적으로 **뉴스레터** 서비스에 대한 프로필을 가입할 수 있습니다. 이 개인화 블록은 필요에 따라 변경할 수 있습니다. 예를 들어 수신자를 다른 서비스로 가입시킬 수 있습니다.

   * 내부 이름(&#39;referrer&#39; here)은 아래와 같이 메시지 전달 스크립트에서 사용됩니다.
   >[!NOTE]
   >
   >배달 템플릿에 대한 자세한 내용은 [이 페이지를](../../delivery/using/about-templates.md) 참조하십시오.

1. 구독 메시지를 전달하기 위한 두 번째 스크립트를 만듭니다.

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

1. 대회 양식을 게시하고 초기 타겟의 수신자에게 초대장을 보냅니다. 그들 중 한 사람이 친구를 초대하면 참조 오퍼 **템플릿을** 기반으로 배달이 만들어집니다.

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   심판은 **[!UICONTROL Administration > Visitors node]**&#x200B;다음 폴더의 방문자 폴더에 추가됩니다.

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   이 프로필에는 레퍼러가 입력한 정보가 포함되어 있습니다. 양식 스크립트에서 입력한 구성을 기반으로 저장됩니다. 뉴스레터에 가입하기로 결정한 경우 수신자 테이블에 저장됩니다.

