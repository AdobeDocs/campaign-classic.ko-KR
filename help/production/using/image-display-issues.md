---
product: campaign
title: 이미지 표시 문제
description: 이미지 표시 문제
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# 이미지 표시 문제{#image-display-issues}

![](../../assets/v7-only.svg)

보낸 메시지에서 이미지 표시 문제가 발생하면 잘못된 위치에 이유가 연결될 수 있습니다.

* 위치가 일치하지 않거나 이미지가 중복 추적 서버에 올바르게 푸시되지 않았을 수 있습니다. 구성을 확인합니다.
* 이미지는 마케팅 인스턴스의 공용 리소스 폴더에 없을 수 있습니다. 이미지를 리소스 폴더에 업로드하여 문제를 해결하십시오.
* 중간 소싱 아키텍처에서 작업하는 경우: 증명을 전송할 때 오류 없이 이미지를 업로드하고 있는지 확인합니다(분석 로그에 정보가 표시됨).

문제 해결 방법:

1. 이미지를 보여주는 증명을 보냅니다.
1. 인스턴스 설정의 리소스 구성을 확인합니다.
1. 공용 리소스 폴더를 확인하거나 공용 리소스 폴더가 없는 경우 게재에서 참조되는 폴더를 확인합니다.
