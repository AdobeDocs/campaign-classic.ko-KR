---
product: campaign
title: 이미지 표시 문제
description: 이미지 표시 문제
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# 이미지 표시 문제{#image-display-issues}



보낸 메시지에서 이미지 표시 문제가 발생하는 경우, 잘못된 위치에 원인이 연결될 수 있습니다.

* 위치가 일치하지 않거나 이미지가 중복 추적 서버로 올바르게 푸시되지 않았을 수 있습니다. 구성을 확인하십시오.
* 이미지가 마케팅 인스턴스의 공개 리소스 폴더에 없을 수 있습니다. 문제를 해결하기 위해 이미지를 리소스 폴더로 업로드합니다.
* 중간 소싱 아키텍처에서 작업하는 경우 증명을 보낼 때 확인 이미지가 오류 없이 업로드됩니다(정보는 분석 로그에 표시됨).

문제 해결 방법:

1. 이미지를 보여 주는 증명을 보냅니다.
1. 인스턴스 설정에서 리소스 구성이 올바른지 확인합니다.
1. 공용 리소스 폴더를 확인하거나, 공용 리소스 폴더에 없는 경우 게재에서 참조된 폴더를 확인합니다.
