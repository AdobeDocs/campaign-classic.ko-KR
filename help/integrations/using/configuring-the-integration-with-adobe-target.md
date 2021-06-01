---
product: campaign
title: Adobe Target과 통합 구성
description: Adobe Target과 통합 구성
audience: integrations
content-type: reference
topic-tags: adobe-target
exl-id: ae8c680f-52a6-4d00-91cd-44d1c3807546
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Adobe Target과 통합 구성{#configuring-the-integration-with-adobe-target}

## 필수 구성 요소 {#prerequisites}

Adobe Campaign과 Adobe Target 간의 통합을 사용하려면 다음을 수행해야 합니다.

* Adobe Experience Cloud 및 Adobe Target 조직
* Adobe Campaign과의 연결을 설정하기 위해 지정된 Adobe Target rawbox

## Adobe Campaign 구성 {#configuring-adobe-campaign}

Adobe Campaign을 구성하려면:

1. **[!UICONTROL Integration with the Adobe Experience Cloud]** 표준 패키지를 설치합니다. 통합 패키지를 설치하는 것은 표준 패키지를 설치하는 것과 같습니다. 표준 패키지는 [패키지 가져오기](../../platform/using/working-with-data-packages.md#importing-packages) 섹션에 자세히 설명되어 있습니다. 이를 통해 디지털 자산 관리자를 통해 공유 자산에 액세스할 수 있습니다.
1. IMS(Adobe ID 연결 서비스)를 통해 연결을 활성화하여 이메일에서 Adobe Experience Cloud을 통해 공유된 이미지를 사용합니다. [IMS](../../integrations/using/about-adobe-id.md)에 대한 섹션을 참조하십시오.
1. **[!UICONTROL Administration > Platform > Options]**&#x200B;에서 Adobe Target에 대한 서버 및 조직(테넌트) 옵션을 구성합니다.

   * **[!UICONTROL TNT_EdgeServer]** :통합에 사용되는 Adobe Target 서버입니다. 이 옵션은 기본적으로 이미 선택되어 있습니다. 이 값은 Adobe Target **[!UICONTROL Domain Server]** 다음에 **/m2** 값이 옵니다. 예:**tt.omtrdc.net/m2**
   * **[!UICONTROL TNT_TenantName]** :Adobe Target 조직 이름. 이 값은 Adobe Target **[!UICONTROL Client]**&#x200B;의 이름에 해당합니다.
   ![](assets/tar_options.png)
