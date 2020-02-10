---
title: 캠페인 제거
seo-title: 캠페인 제거
description: 캠페인 제거
seo-description: null
page-status-flag: never-activated
uuid: 4e95a576-a2fe-41dd-a03d-e4a3120f8788
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 702253cc-3e1a-44ad-9340-b8588ee86bad
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 캠페인 제거{#uninstalling-campaign}

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

**데비안:**

```
apt purge nlserver6-v7
userdel -r neolane
groupdel neolane
rm -rf /user/local/neolane
```

**Windows:**

이 [페이지를](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md#deleting-and-cleansing-adobe-campaign-previous-version)참조하십시오. 캠페인 설치 폴더를 제거하는 것을 잊지 마십시오.
