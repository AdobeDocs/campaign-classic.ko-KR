---
title: 테스트 추적
seo-title: 테스트 추적
description: 테스트 추적
seo-description: null
page-status-flag: never-activated
uuid: 76d84ab4-b632-4498-96a1-ce9c773ec125
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 4ed23249-4ecf-4e57-91b3-6fae1387bd6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 테스트 추적{#testing-tracking}

미러 페이지, 이메일 로그 및 링크에서 추적을 테스트할 수 있습니다. 이렇게 하려면:

1. 테스트에 사용할 새 이메일 배달을 만듭니다.
1. 이메일을 받을 사용자를 지정합니다. 이 사용자는 이메일을 열고 포함된 링크를 클릭해야 하므로 제어하는 테스트 수신자 주소를 선택해야 합니다.
1. 이메일 컨텐츠에 미러 페이지(MirrorPage) 개인화 블록을 추가합니다.
1. 미러 페이지에 대한 링크가 포함된 배달을 보냅니다.
1. 이메일을 받으면 해당 이메일을 열고 미러 페이지 링크를 클릭합니다.
1. 미러 페이지로 올바르게 리디렉션된 후 관리 > 기술 **워크플로우** 폴더에 액세스하고 추적 **워크플로우를** 엽니다.
1. 워크플로우를 시작하고 스케줄러 **작업을** 마우스 오른쪽 단추로 클릭하고 지금 **보류 중인 작업 실행을 선택합니다**.
1. 30초 정도 기다린 다음 감사 **탭을** 선택합니다. 하나 이상의 추적 로그 레코드가 있는지 확인합니다.

   새 **로그가** 표시되지 않으면 새로 고침을 클릭합니다.

1. 테스트에 사용한 수신자의 프로필 페이지로 이동하여 추적 **탭을 선택합니다** . 일부 레코드는 유형 **열에 미러 페이지** 값과 함께 **표시되어야** 합니다.

   >[!NOTE]
   >
   >받는 사람의 프로필 페이지는 기본적으로 프로필 및 대상 **> 수신자** 폴더에 있습니다.

   이메일 로그 추적을 확인하려면 [열기]와 [ **유형** ] **[!UICONTROL Email click]** 열에서 값을 **찾습니다** .

   열려 있는 로그가 나타나지 않으면 전달으로 이동하여 해당 **속성에** 액세스하여 추적 **및** 옵션 활성화를 **[!UICONTROL Opens tracking]** 모두선택해야 합니다.

