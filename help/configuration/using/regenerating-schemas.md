---
title: 스키마 다시 생성
seo-title: 스키마 다시 생성
description: 스키마 다시 생성
seo-description: null
page-status-flag: never-activated
uuid: 455c37f1-cbaf-4503-b2e9-5eec7fad6e97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 0f7c835e-b429-422b-87ae-1234c7dd8fe6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 스키마 다시 생성{#regenerating-schemas}

스키마를 수정하고 수정 내용을 저장하면 확장 스키마가 자동으로 생성됩니다. 그러나 수정 사항을 적용하려면 스키마를 수동으로 다시 생성해야 할 수도 있습니다. 이렇게 하려면:

1. 재생성해야 하는 스키마를 선택합니다.
1. 마우스 오른쪽 버튼을 클릭하고 **[!UICONTROL Actions > Regenerate selected schemas...]** 을 선택합니다.
1. 을 **[!UICONTROL OK]** 클릭하여 프로세스를 확인하고 실행합니다.

그런 다음 미리 보기 및 문서 탭에서 생성된 스키마의 구조를 확인할 수 있습니다. 자세한 내용은 원칙 [섹션을 참조하십시오](../../configuration/using/data-schemas.md#principles) .

>[!NOTE]
>
>모든 스키마를 강제로 재생성해야 하는 경우, 예를 들어 역방향 링크에서 특정 종속성 문제를 해결하기 위해 Adobe Campaign 애플리케이션 서버에서 다음 명령을 실행할 수 있습니다.
>
>**nlserver config -postupgrade -instance:&#39;&lt;instance_name>&#39; -force**
>
>그런 다음 Adobe Campaign 응용 프로그램 서버를 다시 시작하고 클라이언트 콘솔에 연결 끊기/다시 연결해야 합니다.
