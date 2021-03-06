---
product: campaign
title: Campaign 제거
description: Campaign 제거 방법 알아보기
audience: installation
content-type: reference
topic-tags: appendices
exl-id: e2b026ba-aaf3-443d-8c36-c908288a14fd
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 19%

---

# Campaign 제거{#uninstalling-campaign}

![](../../assets/v7-only.svg)

>[!CAUTION]
>
>이러한 절차는 영구적으로 Adobe Campaign을 제거합니다. 모든 데이터가 손실됩니다.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Debian:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

다음을 참조하십시오 [페이지](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). Campaign 설치 폴더를 제거하는 것을 잊지 마십시오.
