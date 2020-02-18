---
title: 외부 데이터베이스 액세스
seo-title: 외부 데이터베이스 액세스
description: 외부 데이터베이스 액세스
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# 데이터 매핑 정의 {#defining-data-mapping}

Adobe Campaign을 사용하면 외부 테이블의 데이터에 대한 매핑을 정의할 수 있습니다.

이렇게 하려면 외부 테이블의 스키마가 생성되면 이 테이블의 데이터를 배달 대상으로 사용하려면 새 배달 매핑을 만들어야 합니다.

이렇게 하려면 다음 단계를 적용합니다.

1. 새 배달 매핑을 만들고 방금 만든 스키마와 같은 타깃팅 차원을 선택합니다.

   ![](assets/wf_new_mapping_create_fda.png)

1. 배달 정보가 저장되는 필드(성, 이름, 이메일, 주소 등)를 지정합니다.

   ![](assets/wf_new_mapping_define_join.png)

1. 확장 스키마를 쉽게 식별할 수 있도록 확장 스키마의 접미어를 포함하여 정보 저장 매개변수를 지정합니다.

   ![](assets/wf_new_mapping_define_names.png)

   제외(**제외**)를 저장할지, 메시지(**브로드캐스트**)를 포함할지, 아니면 별도의 테이블에 저장할지를 선택할 수 있습니다.

   이 배달 매핑(**trackinglog**)에 대한 추적을 관리할지 여부를 선택할 수도 있습니다.

1. 그런 다음 사용할 익스텐션을 선택합니다. 확장 유형은 플랫폼의 매개 변수 및 옵션에 따라 다릅니다(라이선스 계약 보기).

   ![](assets/wf_new_mapping_define_extensions.png)

   배달 매핑 만들기를 시작하려면 **[!UICONTROL Save]** 단추를 클릭합니다.연결된 모든 테이블은 선택한 매개변수를 기준으로 자동으로 생성됩니다.
