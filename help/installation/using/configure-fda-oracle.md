---
solution: Campaign Classic
product: campaign
title: oracle 액세스 권한 구성
description: FDA에서 Oracle에 대한 액세스를 구성하는 방법 살펴보기
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# oracle {#configure-access-to-oracle}에 대한 액세스 구성

캠페인 [통합 데이터 액세스](../../installation/using/about-fda.md)(FDA) 옵션을 사용하여 외부 데이터베이스에 저장된 정보를 처리할 수 있습니다. oracle에 대한 액세스를 구성하려면 아래 단계를 따르십시오.

1. [Linux](#oracle-linux) 또는 [Windows](#azure-windows)에서 Oracle 구성
1. Campaign에서 Oracle [외부 계정](#oracle-external) 구성

## Linux의 oracle {#oracle-linux}

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

1. 사용 중인 Oracle 버전에 해당하는 Oracle 전체 클라이언트를 설치합니다.
1. TNS 정의를 설치에 추가합니다. 이렇게 하려면 /etc/oracle 저장소의 **tnsnames.ora** 파일에 지정합니다. 이 저장소가 없으면 이 저장소를 만듭니다.

   그런 다음 새 TNS_ADMIN 환경 변수를 만듭니다.TNS_ADMIN=/etc/oracle을 내보내고 시스템을 다시 시작합니다.

1. oracle을 Adobe Campaign 서버(nlserver)에 통합합니다. 이렇게 하려면 Adobe Campaign 서버 트리 구조의 &quot;nl6&quot; 폴더에 **customer.sh** 파일이 있으며 Oracle 라이브러리에 대한 링크가 포함되어 있는지 확인하십시오.

   예를 들어 11.2에 있는 클라이언트의 경우

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >이러한 값(특히 ORACLE_HOME)은 설치 저장소에 따라 다릅니다. 이러한 값을 참조하기 전에 트리 구조를 확인해야 합니다.

1. oracle에 필요한 라이브러리 설치:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. 그런 다음 Campaign Classic에서 [!DNL Oracle] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#oracle-external)을 참조하십시오.

## Windows {#oracle-windows}의 oracle

FDA에서 Oracle 외부 데이터베이스에 연결하려면 Adobe Campaign 서버에 아래 추가 구성이 필요합니다.

1. oracle 클라이언트를 설치합니다.

1. C:Oracle 폴더에서 TNS 정의를 포함하는 **tnsnames.ora** 파일을 만듭니다.

1. C:Oracle을 값으로 사용하여 TNS_ADMIN 환경 변수를 추가하고 시스템을 다시 시작합니다.

1. 그런 다음 Campaign Classic에서 [!DNL Oracle] 외부 계정을 구성할 수 있습니다. 외부 계정을 구성하는 방법에 대한 자세한 내용은 [이 섹션](#oracle-external)을 참조하십시오.

## Oracle 외부 계정 {#oracle-external}

[!DNL Oracle] 외부 계정을 사용하면 Campaign 인스턴스를 Oracle 외부 데이터베이스에 연결할 수 있습니다.

1. 캠페인 **[!UICONTROL Explorer]**&#x200B;에서 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**&#x200B;을(를) 선택합니다.

1. **[!UICONTROL New]**&#x200B;을 선택합니다.

1. 외부 계정의 **[!UICONTROL Type]**&#x200B;으로 **[!UICONTROL External database]**&#x200B;을 선택합니다.

1. **[!UICONTROL Oracle]** 외부 계정을 구성합니다. 다음을 지정해야 합니다.

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**:DNS 이름

   * **[!UICONTROL Account]**:사용자 이름

   * **[!UICONTROL Password]**:사용자 계정 암호

   * **[!UICONTROL Time zone]**:서버 시간대

   ![](assets/oracle_config.png)

