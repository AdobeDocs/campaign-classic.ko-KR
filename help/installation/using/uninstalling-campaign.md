---
solution: Campaign Classic
product: campaign
title: Campaign 제거
description: Campaign 제거 방법 살펴보기
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 13%

---


# Campaign 제거{#uninstalling-campaign}

>[!CAUTION]
>
>이러한 절차는 Adobe Campaign을 영구적으로 제거합니다. 모든 데이터가 손실됩니다.

**RHEL:**

```
rpm -e nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**디비안:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

Refer to this [page](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version). 캠페인 설치 폴더를 제거하는 것을 잊지 마십시오.
