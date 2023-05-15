---
product: campaign
title: 암호 분실
description: 암호 분실
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 064eb41f-6685-4ac1-adc5-40f9d5a2f96d
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 8%

---

# 암호 분실{#lost-password}



분실된 암호를 변경하거나 복구할 수 있습니다.
다음 두 가지 가능한 시나리오가 있습니다.

* [Adobe Campaign 연산자에 의해 암호 분실](#password-lost-by-campaign-operator)
* [내부 암호 분실](#internal-password-lost) (온-프레미스 고객만 해당)

## Campaign 연산자에 의해 암호 분실 {#password-lost-by-campaign-operator}

Adobe Campaign 연산자가 암호를 잃어버리면 변경할 수 있습니다.
이렇게 하려면 아래 단계를 수행합니다:

1. 관리자 권한이 있는 연산자를 통해 연결합니다.
1. 연산자를 마우스 오른쪽 단추로 클릭합니다.
1. 선택 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]**.

   ![](assets/operator-passwd.png)

1. 연산자의 새 암호를 설정합니다. 연산자가 처음 다시 연결할 때 암호를 변경하는 것이 좋습니다.

## 내부 암호 분실 {#internal-password-lost}

>[!NOTE]
>
>이 섹션은 온-프레미스 고객에게만 적용됩니다.

내부 암호가 손실되면 다시 초기화해야 합니다.
이렇게 하려면 다음 절차를 적용합니다.

1. 편집 **/usr/local/neolane/nl6/conf/serverConf.xml** 파일.

1. 로 이동합니다. **internalPassword** 줄.

   ```
   <!-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword="myPassword"/>
   ```

1. 이 경우 문자열을 따옴표로 삭제합니다. **myPassword**

   따라서 다음 라인을 얻을 수 있습니다.

   ```
   !-- XTK authentication mode internalPassword : Password of internal account -->
   <xtk internalPassword=""/
   ```

1. 변경 내용을 저장하고 파일을 닫습니다.

1. 새 암호를 구성합니다. 이렇게 하려면 다음 명령을 입력합니다.

   ```
   nlserver config -internalpassword
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   Enter current password.
   Password: (empty)
   Enter the new password.
   Password: 
   Confirmation 
   ```

1. 이제 새 암호를 사용하여 연결할 수 있습니다 **내부** 모드.
