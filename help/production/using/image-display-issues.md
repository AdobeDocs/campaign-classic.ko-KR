---
title: 이미지 표시 문제
seo-title: 이미지 표시 문제
description: 이미지 표시 문제
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 이미지 표시 문제{#image-display-issues}

보낸 메시지에서 이미지 표시 문제가 발생하면 원인은 잘못된 위치에 연결되어 있을 수 있습니다.

* 위치가 일치하지 않거나 이미지가 중복 추적 서버에 올바르게 푸시되지 않았을 수 있습니다.구성을 확인합니다.
* 이미지는 마케팅 인스턴스의 공용 리소스 폴더에 없을 수 있습니다.리소스 폴더에 이미지를 업로드하여 문제를 해결하십시오.
* 중간 소싱 아키텍처에서 작업하는 경우:교정본을 전송할 때 오류 없이 이미지를 업로드합니다(분석 로그에 정보가 표시됨).

문제 해결 방법:

1. 이미지를 보여줄 수 있는 증거를 전송합니다.
1. 인스턴스 설정의 리소스 구성이 올바른지 확인합니다.
1. 공용 리소스 폴더를 확인하거나, 공용 리소스 폴더에 없으면 배달에서 참조된 폴더를 확인하십시오.

