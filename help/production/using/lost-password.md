---
title: 암호 분실
seo-title: 암호 분실
description: 암호 분실
seo-description: null
page-status-flag: never-activated
uuid: caac68bf-abdc-45da-9697-b689ebd37002
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: d52eeadc-19c6-4d48-995a-1c1f2ca3b5ec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# 암호 분실{#lost-password}

분실 암호를 변경하거나 복구할 수 있습니다.

다음과 같은 두 가지 가능한 시나리오가 있습니다.

* Adobe Campaign 운영자가 암호를 분실했습니다.

   이 경우 해당 운영자의 암호를 변경할 수 있습니다. 이렇게 하려면 관리자 권한이 있는 연산자를 통해 연결하고 연산자를 마우스 오른쪽 단추로 클릭한 다음 **[!UICONTROL Actions]** > **[!UICONTROL Reset password]** 을 선택하고 연산자의 새 암호를 설정합니다. 운영자가 처음 다시 연결할 때 암호를 변경하는 것이 좋습니다.

   ![](assets/operator-passwd.png)

* **내부** 암호 손실(온-프레미스 고객만 해당).

   내부 **** 암호가 손실된 경우 다시 초기화해야 합니다. 이렇게 하려면 다음 절차를 적용합니다.

   1. /usr/local/neolane/nl6/conf/serverConf.xml **파일을** 편집합니다.
   1. internalPassword **줄로** 이동합니다.

      ```
      <!-- XTK authentication mode internalPassword : Password of internal account -->
       <xtk internalPassword="myPassword"/>
      ```

   1. 이 경우 따옴표로 문자열을 삭제합니다. **내 암호**

      따라서 다음 줄을 얻게 됩니다.

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

   1. 이제 새 암호를 사용하여 내부 **모드로 연결할 수** 있습니다.

