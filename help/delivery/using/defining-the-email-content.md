---
product: campaign
title: Adobe Campaign Classic에서 이메일 콘텐츠 정의
description: Adobe Campaign 사용 시 이메일 콘텐츠를 정의하는 방법 알아보기
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email Design
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 64a94982ea1eebc30c652e0025eb0aaa0eab1ce9
workflow-type: tm+mt
source-wordcount: '1943'
ht-degree: 1%

---

# 이메일 콘텐츠 정의 {#defining-the-email-content}

## 발신자 {#sender}

보낸 메시지의 헤더에 표시할 보낸 사람의 이름과 주소를 정의하려면 **[!UICONTROL From]** 링크를 클릭합니다.

![](assets/s_ncs_user_wizard_email02.png)

이 창에서는 전자 메일 메시지 머리글을 만드는 데 필요한 모든 정보를 입력할 수 있습니다. 이러한 정보는 개인화할 수 있습니다. 이렇게 하려면 입력 필드 오른쪽에 있는 버튼을 사용하여 개인화 필드를 삽입합니다.

개인화 필드를 삽입하고 사용하는 방법을 알아보려면 다음을 참조하십시오. [개인화 기본 정보](about-personalization.md) 섹션.

>[!NOTE]
>
>* 기본적으로 발신자의 주소가 회신에 사용됩니다.
>* 헤더 매개 변수는 비워 둘 수 없습니다. 기본적으로 배포 마법사를 구성할 때 입력되는 값이 포함됩니다. [이 섹션](../../installation/using/deploying-an-instance.md)에서 자세히 알아보십시오.
>* 이메일을 보낼 수 있도록 하려면 발신자 주소가 필요합니다(RFC 표준).
>* Adobe Campaign은 입력한 이메일 주소의 구문을 확인합니다.

>[!CAUTION]
>
>게재 문제를 방지하려면 게재 및 답글에 대해 지정된 주소에 해당하는 이메일 계정이 있어야 하며 모니터링해야 합니다. 시스템 관리자에게 문의하십시오.

## 메시지 제목 {#message-subject}

메시지 제목은 해당 필드에 구성됩니다. 필드에 직접 입력하거나 **[!UICONTROL Subject]** 스크립트를 입력하는 링크입니다. 개인화 링크를 사용하여 제목에 데이터베이스 필드를 삽입할 수 있습니다.

>[!IMPORTANT]
>
>메시지 제목은 필수입니다.

![](assets/s_ncs_user_wizard_email_object.png)

필드 콘텐츠는 메시지를 보낼 때 수신자 프로필의 값으로 대체됩니다.

예를 들어, 위의 메시지에서 메시지의 주체는 프로필의 데이터를 사용하여 각 수신자에 대해 개인화됩니다.

>[!NOTE]
>
>개인화 필드 사용은에 나와 있습니다. [개인화 기본 정보](about-personalization.md).

또한 다음과 같이 제목 줄에 이모티콘을 삽입할 수도 있습니다. **[!UICONTROL Insert emoticon]** 팝업 창.

## 메시지 콘텐츠 {#message-content}

>[!IMPORTANT]
>
>개인정보 보호를 위해 모든 외부 리소스에 HTTPS를 사용하는 것이 좋습니다.

메시지 콘텐츠는 게재 구성 창의 아래 섹션에 정의되어 있습니다.

메시지는 기본적으로 수신자 기본 설정에 따라 HTML 또는 텍스트 형식으로 전송됩니다. 모든 메일 시스템에서 메시지가 올바르게 표시되도록 하려면 두 형식 모두의 콘텐츠를 만드는 것이 좋습니다. 자세한 내용은 다음을 참조하십시오. [메시지 형식 선택](email-parameters.md#selecting-message-formats).

* HTML 콘텐츠를 가져오려면 **[!UICONTROL Open]** 단추를 클릭합니다. 소스 코드를 **[!UICONTROL Source]** 하위 탭.

  를 사용하는 경우 [디지털 콘텐츠 편집기](../../web/using/about-campaign-html-editor.md) (DCE): [콘텐츠 템플릿 선택](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

  >[!IMPORTANT]
  >
  >HTML 콘텐츠를 미리 만든 다음 Adobe Campaign으로 가져와야 합니다. HTML 편집기는 콘텐츠 작성용으로 디자인되지 않았습니다.

  다음 **[!UICONTROL Preview]** 하위 탭에서는 수신자에 대한 각 콘텐츠의 렌더링을 볼 수 있습니다. 개인화 필드 및 컨텐츠의 조건부 요소는 선택한 프로필에 대한 해당 정보로 대체됩니다.

  도구 모음 단추를 사용하면 HTML 페이지에 대한 표준 작업 및 서식 매개 변수에 액세스할 수 있습니다.

  ![](assets/s_ncs_user_wizard_email01_138.png)

  Adobe Campaign의 로컬 파일 또는 이미지 라이브러리의 메시지에 이미지를 삽입할 수 있습니다. 이렇게 하려면 **[!UICONTROL Image]** 아이콘을 클릭하고 적절한 옵션을 선택합니다.

  ![](assets/s_ncs_user_wizard_email01_18.png)

  라이브러리 이미지는 **[!UICONTROL Resources>Online>Public resources]** 폴더 트리의 폴더. 도 참조하십시오. [이미지 추가 중](#adding-images).

  도구 모음의 마지막 버튼을 사용하여 개인화 필드를 삽입할 수 있습니다.

  >[!NOTE]
  >
  >개인화 필드 사용은에 나와 있습니다. [개인화 기본 정보](about-personalization.md).

  페이지 하단에 있는 탭에서는 생성 중인 페이지의 HTML 코드를 표시하고 개인화와 함께 메시지 렌더링을 볼 수 있습니다. 이 디스플레이를 시작하려면 다음을 클릭하십시오. **[!UICONTROL Preview]** 및 을(를) 사용하여 수신자 선택 **[!UICONTROL Test personalization]** 단추를 클릭합니다. 정의된 대상에서 수신자를 선택하거나 다른 수신자를 선택할 수 있습니다.

  ![](assets/s_ncs_user_wizard_email01_139.png)

  HTML 메시지의 유효성을 검사할 수 있습니다. 이메일 헤더의 콘텐츠를 볼 수도 있습니다.

  ![](assets/s_ncs_user_wizard_email01_140.png)

* 텍스트 콘텐츠를 가져오려면 **[!UICONTROL Open]** 단추 또는 **[!UICONTROL Text Content]** 탭으로 이동하여 텍스트 형식으로 표시할 때 메시지의 내용을 입력합니다. 도구 모음 단추를 사용하여 콘텐츠에 대한 작업에 액세스합니다. 마지막 버튼을 사용하여 개인화 필드를 삽입할 수 있습니다.

  ![](assets/s_ncs_user_wizard_email01_141.png)

  HTML 형식으로는 **[!UICONTROL Preview]** 페이지 하단의 탭을 사용하여 개인화된 메시지 렌더링을 볼 수 있습니다.

  ![](assets/s_ncs_user_wizard_email01_142.png)


## 대화형 콘텐츠 정의 {#amp-for-email-format}

Adobe Campaign을 사용하면 새로운 대화형 기능을 시도할 수 있습니다 [이메일용 AMP](https://amp.dev/about/email/) 형식 - 특정 조건에서 동적 이메일을 보낼 수 있습니다.

자세한 내용은 [이 섹션](defining-interactive-content.md)을 참조하십시오.

## 콘텐츠 관리 사용 {#using-content-management}

콘텐츠 관리 양식을 사용하여 게재 마법사에서 직접 게재 콘텐츠를 정의할 수 있습니다. 이렇게 하려면 다음에서 사용할 콘텐츠 관리의 게시 템플릿을 참조해야 합니다. **[!UICONTROL Advanced]** 게재 속성 탭.

![](assets/s_ncs_content_in_delivery.png)

추가 탭에서는 콘텐츠 관리 규칙에 따라 자동으로 통합되고 형식이 지정된 콘텐츠를 입력할 수 있습니다.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Adobe Campaign의 컨텐츠 관리에 대한 자세한 내용은 [이 섹션](about-content-management.md).

## 이모티콘 삽입 {#inserting-emoticons}

이메일 콘텐츠에 이모티콘을 삽입할 수 있습니다.

1. 다음을 클릭합니다. **[!UICONTROL Insert emoticon]** 아이콘.
1. 팝업 창에서 이모티콘을 선택합니다.

   ![](assets/emoticon_4.png)

1. 다음을 클릭합니다. **[!UICONTROL Close]** 완료되면 버튼을 누릅니다.

이모티콘 목록을 사용자 지정하려면 다음을 참조하십시오. [페이지](customizing-emoticon-list.md).

## 이미지 추가 {#adding-images}

HTML 형식 이메일 게재에 이미지가 포함될 수 있습니다. 게재 마법사에서 이미지가 포함된 HTML 페이지를 가져오거나 를 통해 HTML 편집기를 사용하여 직접 이미지를 삽입할 수 있습니다. **[!UICONTROL Image]** 아이콘.


### 보호 기능 {#img-guardrails}

성능 문제를 방지하기 위해 이메일에 포함된 이미지는 100MB를 초과할 수 없습니다. 기본적으로 설정된 이 제한은 `NmsDelivery_MaxDownloadedImageSize` 옵션을 선택합니다. 그러나 Adobe은 이메일 게재에서 큰 이미지를 피하는 것을 강력히 권장합니다.

다음에서 자세히 알아보기 [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery).

### 이미지 유형 {#img-types}

이미지는 다음과 같을 수 있습니다.

* 로컬 이미지 또는 서버에서 호출된 이미지
* Adobe Campaign 공용 리소스 라이브러리에 저장된 이미지

  공용 리소스는 **[!UICONTROL Resources > Online]** Adobe Campaign 계층 구조의 노드입니다. 라이브러리로 그룹화되고 이메일 메시지에 포함될 수 있지만, 캠페인이나 작업 또는 컨텐츠 관리에도 사용할 수 있습니다.

* Adobe Experience Cloud과 공유된 에셋. [이 섹션](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md)을 참조하십시오.

### 이미지 삽입 및 관리 {#manage-images}

게재 마법사를 사용하여 로컬 이미지 또는 라이브러리에 저장된 이미지를 메시지 콘텐츠에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Image]** HTML 단추를 클릭합니다.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>수신자가 수신한 메시지에 포함된 이미지를 볼 수 있으려면 이러한 메시지는 외부에서 액세스할 수 있는 서버에서 사용할 수 있어야 합니다.

게재 마법사를 통해 이미지를 관리하려면 다음 작업을 수행하십시오.

1. 다음을 클릭합니다. **[!UICONTROL Tracking & Images]** 아이콘을 클릭합니다.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. 선택 **[!UICONTROL Upload images]** 다음에서 **[!UICONTROL Images]** 탭.
1. 그런 다음 이메일 메시지에 이미지를 포함할지 여부를 선택할 수 있습니다.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* 게재 분석 단계를 기다리지 않고 이미지를 수동으로 업로드할 수 있습니다. 이렇게 하려면 **[!UICONTROL Upload the images straightaway...]** 링크를 클릭합니다.
* 추적 서버의 이미지에 액세스하기 위한 다른 경로를 지정할 수 있습니다. 이렇게 하려면 **[!UICONTROL Images URL]** 필드. 이 값은 설치 마법사의 매개 변수에 정의된 값을 재정의합니다.

게재 마법사에 포함된 이미지가 있는 HTML 콘텐츠를 열면 메시지가 게재 매개 변수에 따라 이미지를 즉시 업로드할 수 있는 옵션을 제공합니다.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
> 이미지 URL은 수동으로 업로드하는 동안 또는 메시지를 보낼 때 수정됩니다.
> 

### 사용 사례: 이미지가 포함된 메시지 보내기 {#uc-images}

다음은 네 가지 이미지가 포함된 게재 샘플입니다.

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

이러한 이미지는 다음 위치에서 확인할 수 있는 대로 로컬 디렉토리 또는 웹 사이트에서 가져옵니다. **[!UICONTROL Source]** 탭.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

다음을 클릭합니다. **[!UICONTROL Tracking & Images]** 아이콘을 클릭한 다음 **[!UICONTROL Images]** 탭에서 메시지의 이미지 검색을 시작합니다.

감지된 각 이미지에 대해 해당 상태를 볼 수 있습니다.

* 이미지가 로컬에 저장되거나 다른 서버에 있는 경우 이 서버가 외부(예: 인터넷 사이트)에서 표시되더라도 다음과같이 감지됩니다. **[!UICONTROL Not yet online]**.
* 이미지가 다음으로 감지됨 **[!UICONTROL Already online]** 다른 게재를 만드는 동안 더 일찍 업로드된 경우.
* 배포 마법사에서 이미지 감지가 활성화되지 않은 URL을 정의할 수 있습니다. 이러한 이미지를 업로드하면 다음과 같이 됩니다. **[!UICONTROL Skipped]**.

>[!NOTE]
>
>이미지는 액세스 경로가 아닌 콘텐츠로 식별됩니다. 즉, 이전에 다른 이름 또는 다른 디렉토리에 업로드된 이미지는 다음과 같이 감지됩니다. **[!UICONTROL Already online]**.

분석 단계에서는 미리 업로드해야 하는 로컬 이미지를 제외하고 외부에서 액세스할 수 있도록 이미지가 자동으로 서버에 업로드됩니다.

다른 Adobe Campaign 운영자가 볼 수 있도록 미리 작업하고 이미지를 업로드할 수 있습니다. 공동 작업을 하는 경우 이 기능이 유용할 수 있습니다. 이렇게 하려면 다음을 클릭하십시오. **[!UICONTROL Upload the images straightaway...]** 이미지를 서버에 업로드합니다.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>이메일에 있는 이미지의 URL과 특히 해당 이름이 수정됩니다.

이미지가 온라인 상태가 되면 다음에서 해당 이름 및 경로에 대한 변경 사항을 볼 수 있습니다. **[!UICONTROL Source]** 메시지 탭.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

다음을 선택하는 경우 **[!UICONTROL Include the images in the email]**, 해당 열에 포함할 이미지를 선택할 수 있습니다.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>로컬 이미지가 메시지에 포함된 경우 메시지 소스 코드에 대한 변경 사항을 확인해야 합니다.

## 개인화된 바코드 삽입{#insert-a-barcode}

바코드 생성 모듈을 사용하면 2D 바코드를 포함하여 많은 공통 표준을 준수하는 여러 유형의 바코드를 만들 수 있습니다.

고객 기준으로 정의한 값을 이용하여 바코드를 비트맵으로 동적으로 생성할 수 있다. 개인화된 바코드를 이메일 캠페인에 포함할 수 있습니다. 수신자는 메시지를 인쇄하고 발행 회사에 표시하여 검색할 수 있습니다(예: 체크아웃 시).

이메일에 바코드를 삽입하려면 표시하려는 콘텐츠에 커서를 놓은 다음 개인화 버튼을 클릭합니다. **[!UICONTROL Include > Barcode...]**&#x200B;을(를) 선택합니다.

![](assets/barcode_insert_14.png)

그런 다음 필요에 맞게 다음 요소를 구성합니다.

1. 바코드 유형을 선택합니다.

   * 1D 형식의 경우 Adobe Campaign에서 Codabar, Code 128, GS1-128(이전 EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET 및 Royal Mail(RM4SCC) 형식을 사용할 수 있습니다.

     1D 바코드의 예:

     ![](assets/barcode_insert_08.png)

   * DataMatrix 및 PDF417 유형은 2D 포맷과 관련이 있습니다.

     2D 바코드의 예:

     ![](assets/barcode_insert_09.png)

   * QR 코드를 삽입하려면 이 유형을 선택하고 적용할 오류 수정 비율을 입력합니다. 이 비율은 반복되는 정보의 양과 악화 허용 한도를 정의합니다.

     ![](assets/barcode_insert_06.png)

     QR 코드의 예:

     ![](assets/barcode_insert_12.png)

1. 이메일에 삽입할 바코드의 크기를 입력합니다. 크기를 구성하면 바코드의 크기를 x1에서 x10으로 늘리거나 줄일 수 있습니다.
1. 다음 **[!UICONTROL Value]** 필드를 사용하면 바코드의 값을 정의할 수 있습니다. 값은 특별 오퍼와 일치할 수 있으며 기준의 함수가 될 수 있습니다. 이 값은 고객에 연결된 데이터베이스 필드의 값이 될 수 있습니다.

   이 예에서는 수신자의 계정 번호가 추가된 EAN-8 유형 바코드를 보여 줍니다. 이 계정 번호를 추가하려면 오른쪽에 있는 개인화 버튼을 클릭합니다. **[!UICONTROL Value]** 필드 및 선택 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 다음 **[!UICONTROL Height]** 필드를 사용하면 각 막대 사이의 공간을 변경하여 바코드의 너비를 변경하지 않고 바코드의 높이를 구성할 수 있습니다.

   바코드의 유형에 따라 제한적으로 항목을 제어할 수 없습니다. 바코드 값이 올바르지 않으면 다음에만 표시됩니다 **미리 보기** 바코드가 빨간색으로 교차되는 모드입니다.

   >[!NOTE]
   >
   >바코드에 할당된 값은 유형에 따라 다릅니다. 예를 들어 EAN-8 형식에는 정확히 8개의 숫자가 있어야 합니다.
   >
   >의 오른쪽에 있는 개인화 버튼 **[!UICONTROL Value]** 필드를 사용하면 값 자체에 데이터를 추가할 수 있습니다. 이렇게 하면 바코드 표준에서 허용하는 한 바코드가 강화됩니다.
   >
   >예를 들어, GS1-128을 사용하는 경우 바코드를 입력하고 값 외에 수신자의 계좌 번호를 입력하려면 개인화 버튼을 클릭하고 을 선택합니다. **[!UICONTROL Recipient > Account number]**. 선택한 수신자의 계좌 번호를 올바르게 입력하면 바코드가 이를 고려합니다.

이러한 요소가 구성되면 이메일을 마무리하여 보낼 수 있습니다. 오류를 방지하려면 게재를 수행하기 전에 **[!UICONTROL Preview]** 탭.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>바코드의 값이 올바르지 않으면 비트맵이 빨간색으로 교차하여 표시됩니다.

![](assets/barcode_insert_11.png)
