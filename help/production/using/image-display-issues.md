---
solution: Campaign Classic
product: campaign
title: 이미지 표시 문제
description: 이미지 표시 문제
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 6%

---


# 이미지 표시 문제{#image-display-issues}

보낸 메시지에서 이미지 표시 문제가 발생하는 경우 원인은 잘못된 위치에 연결되어 있을 수 있습니다.

* 위치가 일치하지 않거나 이미지가 중복된 추적 서버로 올바르게 푸시되지 않았을 수 있습니다.구성을 확인하십시오.
* 이미지는 마케팅 인스턴스의 공용 리소스 폴더에 있을 수 없습니다.리소스 폴더에 이미지를 업로드하여 문제를 해결하십시오.
* 중간 소싱 아키텍처에서 작업하는 경우:교정본을 보낼 때 확인 이미지는 오류 없이 업로드됩니다(분석 로그에 정보가 표시됨).

문제 해결 방법:

1. 이미지를 보여줄 수 있는 증거를 전송합니다.
1. 인스턴스 설정의 리소스 구성이 올바른지 확인합니다.
1. 공용 리소스 폴더를 확인하거나, 공용 리소스 폴더에 없으면 배달에서 참조된 폴더를 확인하십시오.

