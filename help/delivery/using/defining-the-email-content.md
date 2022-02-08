---
product: campaign
title: Adobe Campaign Classic에서 이메일 콘텐츠 정의
description: Adobe Campaign Classic을 사용할 때 이메일 콘텐츠를 정의하는 방법을 알아봅니다.
feature: Email Design
exl-id: 46212929-fd2d-44a2-897e-35f98e88af36
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1990'
ht-degree: 1%

---

# 이메일 콘텐츠 정의 {#defining-the-email-content}

![](../../assets/common.svg)

## 보낸 사람 {#sender}

보낸 메시지 헤더에 표시될 발신자의 이름과 주소를 정의하려면 **[!UICONTROL From]** 링크를 클릭합니다.

![](assets/s_ncs_user_wizard_email02.png)

이 창에서는 전자 메일 메시지 헤더를 만드는 데 필요한 모든 정보를 입력할 수 있습니다. 이러한 정보는 개인화할 수 있습니다. 이렇게 하려면 입력 필드 오른쪽의 버튼을 사용하여 개인화 필드를 삽입합니다.

개인화 필드를 삽입 및 사용하는 방법을 알아보려면 [개인화 기본 정보](about-personalization.md) 섹션을 참조하십시오.

>[!NOTE]
>
>* 발신자의 주소는 기본적으로 회신에 사용됩니다.
>* 헤더 매개 변수는 비워 둘 수 없습니다. 기본적으로 배포 마법사를 구성할 때 값 입력이 포함됩니다. 자세한 내용은 [설치 안내서](../../installation/using/deploying-an-instance.md).
>* 전자 메일을 보낼 수 있도록 하려면 보낸 사람의 주소가 필수입니다(RFC 표준).
>* Adobe Campaign은 입력한 이메일 주소 구문을 확인합니다.


>[!IMPORTANT]
>
>ISP(인터넷 액세스 공급자)가 원치 않는 이메일(스팸)을 방지하기 위해 구현하는 확인 컨텍스트에서, Adobe은 게재 및 답글에 지정된 주소에 해당하는 이메일 계정을 만드는 것을 권장합니다. 메시징 시스템 관리자에게 문의하십시오.

## 메시지 제목 {#message-subject}

메시지의 제목은 해당 필드에 구성됩니다. 필드에 직접 입력하거나 **[!UICONTROL Subject]** 링크를 클릭하여 스크립트를 입력합니다. 개인화 링크를 사용하면 제목에 데이터베이스 필드를 삽입할 수 있습니다.

>[!IMPORTANT]
>
>메시지 제목은 필수입니다.

![](assets/s_ncs_user_wizard_email_object.png)

메시지가 전송될 때 필드 콘텐츠가 수신자 프로필의 값으로 바뀝니다.

예를 들어 위의 메시지에서 메시지의 제목은 각 수신자에 대해 프로필의 데이터를 개인화합니다.

>[!NOTE]
>
>개인화 필드 사용은 [개인화 기본 정보](about-personalization.md).

를 사용하여 제목 줄에 이모티콘을 삽입할 수도 있습니다 **[!UICONTROL Insert emoticon]** 팝업 창.

## 메시지 콘텐츠 {#message-content}

>[!IMPORTANT]
>
>개인 정보용으로 모든 외부 리소스에 HTTPS를 사용하는 것이 좋습니다.

메시지 컨텐츠는 게재 구성 창의 하위 섹션에 정의됩니다.

메시지는 수신자 환경 설정에 따라 기본적으로 HTML 또는 텍스트 형식으로 전송됩니다. 모든 메일 시스템에서 메시지를 올바르게 표시할 수 있도록 두 형식 모두에서 컨텐츠를 만드는 것이 좋습니다. 자세한 내용은 [메시지 형식 선택](#selecting-message-formats).

* HTML 컨텐츠를 가져오려면 **[!UICONTROL Open]** 버튼을 클릭합니다. 소스 코드를 **[!UICONTROL Source]** 하위 탭.

   를 사용하는 경우 [디지털 콘텐츠 편집기](../../web/using/about-campaign-html-editor.md) (DCE) [컨텐츠 템플릿 선택](../../web/using/use-case--creating-an-email-delivery.md#step-3---selecting-a-content).

   >[!IMPORTANT]
   >
   >HTML 컨텐츠를 미리 만든 다음 Adobe Campaign으로 가져와야 합니다. HTML 편집기는 콘텐츠 작성을 위해 설계되지 않았습니다.

   다음 **[!UICONTROL Preview]** 하위 탭에서는 수신자에 대한 각 컨텐츠 렌더링을 볼 수 있습니다. 개인화 필드 및 콘텐츠의 조건부 요소는 선택한 프로필에 대한 해당 정보로 대체됩니다.

   도구 모음 단추를 사용하면 HTML 페이지의 표준 작업 및 형식 매개 변수에 액세스할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email01_138.png)

   로컬 파일의 메시지 또는 Adobe Campaign의 이미지 라이브러리에서 이미지를 삽입할 수 있습니다. 이렇게 하려면 **[!UICONTROL Image]** 아이콘을 클릭하고 적절한 옵션을 선택합니다.

   ![](assets/s_ncs_user_wizard_email01_18.png)

   라이브러리 이미지는 **[!UICONTROL Resources>Online>Public resources]** 폴더 트리의 폴더. 또한 [이미지 추가](#adding-images).

   도구 모음의 마지막 버튼을 사용하여 개인화 필드를 삽입할 수 있습니다.

   >[!NOTE]
   >
   >개인화 필드 사용은 [개인화 기본 정보](about-personalization.md).

   페이지 하단의 탭에서는 만들어지는 페이지의 HTML 코드를 표시하고 개인화를 사용하여 메시지 렌더링을 볼 수 있습니다. 이 디스플레이를 시작하려면 **[!UICONTROL Preview]** 을(를) 사용하여 수신자를 선택하고 **[!UICONTROL Test personalization]** 단추를 누릅니다. 정의된 대상에서 수신자를 선택하거나 다른 수신자를 선택할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email01_139.png)

   HTML 메시지의 유효성을 검사할 수 있습니다. 이메일 헤더의 콘텐츠를 볼 수도 있습니다.

   ![](assets/s_ncs_user_wizard_email01_140.png)

* 텍스트 컨텐츠를 가져오려면 **[!UICONTROL Open]** 버튼 또는 **[!UICONTROL Text Content]** 텍스트 형식으로 표시할 때 메시지 콘텐츠를 입력할 수 있습니다. 도구 모음 단추를 사용하여 내용에 대한 작업에 액세스합니다. 마지막 버튼을 사용하면 개인화 필드를 삽입할 수 있습니다.

   ![](assets/s_ncs_user_wizard_email01_141.png)

   HTML 형식에 대해 을(를) 클릭합니다. **[!UICONTROL Preview]** 개인화를 사용하여 메시지 렌더링을 볼 수 있도록 페이지 하단에 있는 탭.

   ![](assets/s_ncs_user_wizard_email01_142.png)


## 대화형 콘텐츠 정의 {#amp-for-email-format}

Adobe Campaign을 사용하면 새로운 대화형 기능을 사용할 수 있습니다 [이메일용 AMP](https://amp.dev/about/email/) 특정 조건에서 다이내믹 이메일을 보낼 수 있는 형식입니다.

자세한 내용은 [이 섹션](defining-interactive-content.md)을 참조하십시오.

## 콘텐츠 관리 사용 {#using-content-management}

게재 마법사에서 직접 컨텐츠 관리 양식을 사용하여 게재 콘텐츠를 정의할 수 있습니다. 이렇게 하려면 에서 사용할 컨텐츠 관리의 게시 템플릿을 참조해야 합니다. **[!UICONTROL Advanced]** 전달 속성의 탭입니다.

![](assets/s_ncs_content_in_delivery.png)

추가 탭에서는 컨텐츠 관리 규칙에 따라 자동으로 통합되고 형식이 지정되는 컨텐츠를 입력할 수 있습니다.

![](assets/s_ncs_content_in_delivery_edition_tab.png)

>[!NOTE]
>
>Adobe Campaign의 콘텐츠 관리에 대한 자세한 내용은 [이 섹션](about-content-management.md).

## 이모티콘 삽입 {#inserting-emoticons}

이메일 콘텐츠에 이모티콘을 삽입할 수 있습니다.

1. 을(를) 클릭합니다. **[!UICONTROL Insert emoticon]** 아이콘.
1. 팝업 창에서 이모티콘을 선택합니다.

   ![](assets/emoticon_4.png)

1. 을(를) 클릭합니다. **[!UICONTROL Close]** 완료 시 버튼을 클릭합니다.

이모티콘 목록을 사용자 정의하려면 다음을 참조하십시오 [페이지](customizing-emoticon-list.md).

## 이미지 추가 {#adding-images}

HTML 형식 이메일 게재에는 이미지가 포함될 수 있습니다. 게재 마법사에서 이미지가 포함된 HTML 페이지를 가져오거나 를 통해 HTML 편집기를 사용하여 직접 이미지를 삽입할 수 있습니다. **[!UICONTROL Image]** 아이콘.

이미지는 다음 작업을 수행할 수 있습니다.

* 로컬 이미지 또는 서버에서 호출된 이미지
* Adobe Campaign 공용 리소스 라이브러리에 저장된 이미지

   공개 리소스는 **[!UICONTROL Resources > Online]** 노드 아래에 나열된 상태로 남아 있습니다. 라이브러리로 그룹화되어 이메일 메시지에 포함할 수 있지만 캠페인이나 작업 또는 콘텐츠 관리에 사용할 수도 있습니다.

* Adobe Experience Cloud과 공유된 자산. [이 섹션](../../integrations/using/sharing-assets-with-adobe-experience-cloud.md)을 참조하십시오.

>[!IMPORTANT]
>
>게재 마법사를 사용하여 이메일 메시지에 이미지를 포함하려면 공개 리소스 관리를 사용하도록 Adobe Campaign 인스턴스를 구성해야 합니다. 이 절차는 배포 마법사에서 수행할 수 있습니다. 자세한 내용은 [이 섹션](../../installation/using/deploying-an-instance.md) 구성에 대한 자세한 내용을 참조하십시오.

게재 마법사를 사용하여 로컬 이미지 또는 라이브러리에 저장된 이미지를 메시지 콘텐츠에 추가할 수 있습니다. 이렇게 하려면 **[!UICONTROL Image]** HTML 컨텐츠 도구 모음의 단추.

![](assets/s_ncs_user_image_from_library.png)

>[!IMPORTANT]
>
>수신자가 수신한 메시지에 포함된 이미지를 보려면 이러한 메시지를 외부에서 액세스할 수 있는 서버에서 사용할 수 있어야 합니다.

게재 마법사를 통해 이미지를 관리하려면 다음을 수행하십시오.

1. 을(를) 클릭합니다. **[!UICONTROL Tracking & Images]** 아이콘 을 클릭하여 제품에서 사용할 수 있습니다.
   ![](assets/s_ncs_user_email_del_img_param.png)

1. 선택 **[!UICONTROL Upload images]** 에서 **[!UICONTROL Images]** 탭.
1. 그런 다음 이메일 메시지에 이미지를 포함할지 여부를 선택할 수 있습니다.
   ![](assets/s_ncs_user_email_del_img_upload.png)

* 게재 분석 단계를 기다리지 않고 수동으로 이미지를 업로드할 수 있습니다. 이렇게 하려면 **[!UICONTROL Upload the images straightaway...]** 링크를 클릭합니다.
* 추적 서버의 이미지에 액세스할 다른 경로를 지정할 수 있습니다. 이렇게 하려면 다음을 입력합니다. **[!UICONTROL Images URL]** 필드. 이 값은 설치 마법사의 매개 변수에 정의된 값을 재정의합니다.

게재 마법사에서 포함된 이미지가 포함된 HTML 컨텐츠를 열 때 게재 매개 변수에 따라 이미지를 즉시 업로드할 수 있는 옵션이 표시됩니다.

![](assets/s_ncs_user_email_del_img_local.png)

>[!IMPORTANT]
>
>* 이미지 액세스 경로는 수동 업로드 중 또는 메시지를 전송할 때 수정됩니다.
> 
>* 성능 문제를 방지하기 위해 개인화된 URL에서 즉시 다운로드한 이미지를 [첨부 파일](attaching-files.md)로 지정하는 경우 각 이미지 크기는 기본적으로 100,000바이트를 초과할 수 없습니다. 이 권장 임계값은 다음에서 구성할 수 있습니다. [Campaign Classic 옵션 목록](../../installation/using/configuring-campaign-options.md#delivery).


**사용 사례: 이미지로 메시지 보내기**

다음은 4개의 이미지가 포함된 게재 샘플입니다.

![](assets/s_ncs_user_images_in_delivery_wiz_1.png)

이러한 이미지는 로컬 디렉토리 또는 웹 사이트에서 확인할 수 있습니다. **[!UICONTROL Source]** 탭.

![](assets/s_ncs_user_images_in_delivery_wiz_2.png)

을(를) 클릭합니다. **[!UICONTROL Tracking & Images]** 아이콘 다음에 **[!UICONTROL Images]** 탭에서 메시지의 이미지 탐지를 시작합니다.

감지된 각 이미지에 대해 해당 상태를 볼 수 있습니다.

* 이미지가 로컬에 저장되거나 다른 서버에 있는 경우, 이 서버가 외부로부터(예: 인터넷 사이트)로 표시되더라도 **[!UICONTROL Not yet online]**.
* 이미지는 **[!UICONTROL Already online]** 다른 게재를 만드는 동안 이전에 업로드된 경우.
* 배포 마법사에서 이미지 감지가 활성화되지 않은 URL을 정의할 수 있습니다. 이러한 이미지를 업로드하면 **[!UICONTROL Skipped]**.

>[!NOTE]
>
>이미지는 액세스 경로가 아니라 해당 컨텐츠로 식별됩니다. 즉, 이전에 다른 이름 또는 다른 디렉토리에 업로드된 이미지가 **[!UICONTROL Already online]**.

분석 단계 동안, 미리 업로드해야 하는 로컬 이미지를 제외하고 외부에서 액세스할 수 있도록 이미지가 자동으로 서버에 업로드됩니다.

다른 Adobe Campaign 운영자가 볼 수 있도록 미리 작업하고 이미지를 업로드할 수 있습니다. 공동 작업을 하는 경우 이 기능이 유용할 수 있습니다. 이렇게 하려면 **[!UICONTROL Upload the images straightaway...]** 를 눌러 서버에 이미지를 업로드합니다.

![](assets/s_ncs_user_images_in_delivery_wiz_3.png)

>[!NOTE]
>
>전자 메일에 있는 이미지의 URL 및 특히 해당 이름이 수정됩니다.

이미지가 온라인 상태가 되면 **[!UICONTROL Source]** 탭의 메시지를 표시합니다.

![](assets/s_ncs_user_images_in_delivery_wiz_4.png)

선택하는 경우 **[!UICONTROL Include the images in the email]**&#x200B;로 지정하는 경우 해당 열에 포함할 이미지를 선택할 수 있습니다.

![](assets/s_ncs_user_images_in_delivery_wiz_5.png)

>[!NOTE]
>
>로컬 이미지가 메시지에 포함된 경우 메시지 소스 코드의 변경 사항을 확인해야 합니다.

## 개인화된 바코드 삽입{#insert-a-barcode}

바코드 생성 모듈을 사용하면 2D 바코드를 포함하여 다양한 공통 표준을 준수하는 여러 종류의 바코드를 만들 수 있습니다.

고객 기준을 사용하여 정의된 값을 사용하여 바코드를 비트맵으로 동적으로 생성할 수 있습니다. 개인화된 바코드는 이메일 캠페인에 포함할 수 있습니다. 수신자는 메시지를 인쇄하여 스캔을 위해 발행 회사에 표시할 수 있습니다(예를 들어 체크 아웃할 때).

전자 메일에 바코드를 삽입하려면 커서를 표시할 콘텐츠에 놓고 개인화 단추를 클릭합니다. **[!UICONTROL Include > Barcode...]**&#x200B;을(를) 선택합니다.

![](assets/barcode_insert_14.png)

그런 다음 필요에 맞게 다음 요소를 구성합니다.

1. 바코드 유형을 선택합니다.

   * 1D 형식의 경우 Adobe Campaign에서 다음 유형을 사용할 수 있습니다. Codabar, Code 128, GS1-128(이전의 EAN-128), UPC-A, UPC-E, ISBN, EAN-8, Code39, Interleaved 2 of 5, POSTNET 및 Royal Mail(RM4SCC).

      1D 바코드의 예:

      ![](assets/barcode_insert_08.png)

   * DataMatrix 및 PDF417 형식은 2D 형식과 관련이 있습니다.

      2D 바코드의 예:

      ![](assets/barcode_insert_09.png)

   * QR 코드를 삽입하려면 이 유형을 선택하고 적용할 오류 수정 비율을 입력합니다. 이 비율은 반복되는 정보의 양과 열화에 대한 허용한도를 정의합니다.

      ![](assets/barcode_insert_06.png)

      QR 코드의 예:

      ![](assets/barcode_insert_12.png)

1. 전자 메일에 삽입할 바코드의 크기를 입력합니다. 스케일을 구성하면 바코드의 크기를 x1에서 x10으로 늘리거나 줄일 수 있습니다.
1. 다음 **[!UICONTROL Value]** 필드를 사용하면 바코드의 값을 정의할 수 있습니다. 값은 특별 오퍼와 일치할 수 있으며 기준의 기능일 수 있으며, 고객에 연결된 데이터베이스 필드의 값이 될 수 있습니다.

   이 예에서는 수신자의 계정 번호를 추가한 EAN-8 형식의 바코드를 보여 줍니다. 이 계정 번호를 추가하려면 오른쪽의 개인화 단추를 클릭하십시오. **[!UICONTROL Value]** 필드 및 선택 **[!UICONTROL Recipient > Account number]**.

   ![](assets/barcode_insert_15.png)

1. 다음 **[!UICONTROL Height]** 필드를 사용하면 각 막대 사이의 공간을 변경하여 바코드의 너비를 변경하지 않고 바코드의 높이를 구성할 수 있습니다.

   바코드 유형에 따라 제한적인 항목 제어가 없습니다. 바코드 값이 올바르지 않으면 **미리 보기** 바코드가 빨간색으로 교차될 모드

   >[!NOTE]
   >
   >바코드에 할당된 값은 해당 유형에 따라 다릅니다. 예를 들어 EAN-8 유형은 정확히 8개의 숫자를 가집니다.
   >
   >오른쪽에 있는 개인화 단추 **[!UICONTROL Value]** 필드를 사용하면 값 자체에 데이터를 추가할 수 있습니다. 바코드 표준이 바코드를 수락하는 경우 바코드를 강화합니다.
   >
   >예를 들어, GS1-128 유형 바코드를 사용하고 값 외에 수신자의 계정 번호를 입력하려면 개인화 버튼을 클릭하고 을 선택합니다 **[!UICONTROL Recipient > Account number]**. 선택한 수신자의 계좌 번호를 올바르게 입력하면 바코드가 이를 고려합니다.

이러한 요소가 구성되면 전자 메일을 완료하고 보낼 수 있습니다. 오류를 방지하려면 항상 을 클릭하여 게재를 수행하기 전에 콘텐츠가 올바르게 표시되는지 확인하십시오 **[!UICONTROL Preview]** 탭.

![](assets/barcode_insert_10.png)

>[!NOTE]
>
>바코드의 값이 올바르지 않으면 비트맵이 빨간색으로 교차되어 표시됩니다.

![](assets/barcode_insert_11.png)
