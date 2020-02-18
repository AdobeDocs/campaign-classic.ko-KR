---
title: 모바일 앱 채널 설정
seo-title: 모바일 앱 채널 설정
description: 모바일 앱 채널 설정
seo-description: null
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8c4face331ab6d646480322c0f53a7147251aa6

---


# 모바일 애플리케이션에 Campaign SDK 통합 {#integrating-campaign-sdk-into-the-mobile-application}

iOS 및 Android용 캠페인 SDK는 모바일 앱 채널 모듈의 구성 요소 중 하나입니다.

>[!NOTE]
>
>Campaign SDK(이전의 Neolane SDK)를 받으려면 Adobe 고객 지원 센터에 문의하십시오.

SDK의 목표는 모바일 애플리케이션을 Adobe Campaign 플랫폼에 쉽게 통합하는 것입니다.

지원되는 다양한 Android 및 iOS 버전에 대한 자세한 내용은 호환성 [매트릭스를](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#MobileSDK) 참조하십시오.

## 캠페인 SDK 로드 {#loading-campaign-sdk}

* **Android**:neolane_ **sdk-release.aar** 파일은 프로젝트에 연결되어 있어야 합니다.

   다음 권한은 Adobe Campaign 서버에 대한 액세스 권한을 부여합니다.

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
   ```

   다음 권한을 통해 전화의 고유 ID를 복구할 수 있습니다.

   ```
   <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   ```

   SDK 버전 1.0.24부터 이 권한은 Android 6.0 이전 버전에만 사용됩니다.

   SDK 버전 1.0.26에서 이 권한은 더 이상 사용되지 않습니다.

* **iOS에서**:lib **NeolaneSDK.a** 및 **Neolane_SDK.h** 파일은 프로젝트에 연결되어 있어야 합니다. SDK 버전 1.0.24부터 ENABLE_ **BITCODE 옵션이** 활성화됩니다.

   >[!NOTE]
   >
   >SDK 버전 1.0.25의 경우 Neolane_SDK. **h** 파일에서 4개의 아키텍처를 사용할 수 있습니다.

## 통합 설정 선언 {#declaring-integration-settings}

Campaign SDK를 모바일 애플리케이션에 통합하려면 기능 관리자가 개발자에게 다음 정보를 제공해야 합니다.

* **통합 키**:을 클릭하여 Adobe Campaign 플랫폼을 활성화하여 모바일 애플리케이션을 식별합니다.

   >[!NOTE]
   >
   >이 통합 키는 모바일 애플리케이션 전용 서비스의 **[!UICONTROL Information]** 탭에 있는 Adobe Campaign 콘솔에 입력됩니다. Adobe [Campaign에서 모바일 애플리케이션 구성을 참조하십시오](../../delivery/using/configuring-the-mobile-application.md).

* **추적 URL**:는 Adobe Campaign 추적 서버의 주소와 일치합니다.
* **마케팅 URL**:를 클릭하여 구독을 활성화합니다.

* **Android**:

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
   ```

* **iOS에서**:

   ```
   Neolane_SDK *nl = [Neolane_SDK getInstance];
   [nl setMarketingHost:strMktHost];
   [nl setTrackingHost:strTckHost];
   [nl setIntegrationKey:strIntegrationKey];
   ```

## 등록 함수 {#registration-function}

등록 기능을 사용하면 다음 작업을 수행할 수 있습니다.

* 알림 ID 또는 푸시 ID(iOS용 deviceToken 및 Android용 registrationID)를 Adobe Campaign에 보냅니다.
* 조정 키 또는 userKey 복구(예: 이메일 또는 계정 번호)

* **Android**:

   ```
   void registerInNeolane(String registrationId, String userKey, Context context)
   {
    try{
     Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
    } catch (NeolaneException e){
     //...
    } catch (IOException e){
     //...
    }
   }
   ```

   FCM(Firebase Cloud Messaging)을 사용하는 경우 **onTokenRefresh** 함수를 호출할 때 **registerDevice** 함수를 사용하여 사용자의 모바일 장치 토큰의 변경 사항을 Adobe Campaign에 알릴 것을 권장합니다.

   ```
   public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
     @Override
     public void onTokenRefresh() {
       String registrationToken = FirebaseInstanceId.getInstance().getToken();
       NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
       ...
       ...
       // Neolane Registration
       neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
       public void onComplete(String e, Object state) { ... }
       public void onNeolaneException(NeolaneException e, Object state) { ... }
       public void onIOException(IOException e, Object state) { ... }
       });
       ...
       ...
     }
   }
   ```

* **iOS에서**:

   ```
   // Callback called on successful registration to the APNS
   - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
   {
       // Pass the token to Adobe Campaign
       Neolane_SDK *nl = [Neolane_SDK getInstance];
       [nl registerDevice:tokenString:self.userKey:dic];
   }
   ```

## 추적 함수 {#tracking-function}

* **Android**:

   추적 기능을 사용하면 알림 활성화(열기)와 알림 표시(스크린샷)를 추적할 수 있습니다.

   알림 표시를 추적하려면(SDK의 **notifyReceive** 함수를 호출하여 완료) 아래 구현을 따르십시오. FCM(Firebase Cloud Messaging)을 사용하는 경우 Android 시스템에서 **onMessageReceived** 함수를 호출할 **때** notifyReceive 함수를 사용하는 것이 좋습니다.

   ```
   package com.android.YourApplication;
   
   import android.content.Context;
   import android.content.SharedPreferences;
   import android.os.Bundle;
   import android.util.Log;
   
   import com.google.firebase.messaging.FirebaseMessagingService;
   import com.google.firebase.messaging.RemoteMessage;
   
   import java.util.Iterator;
   import java.util.Map;
   import java.util.Map.Entry;
   
   public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
     private static final String TAG = "MyFirebaseMsgService";
   
     @Override
     public void onMessageReceived(RemoteMessage message) {
       Log.d(TAG, "Receive message from: " + message.getFrom());
       Map<String,String> payloadData = message.getData();
       final Bundle extras = new Bundle();
       final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
       while(iter.hasNext())
       {
         final Entry<String, String>  entry =iter.next();
         extras.putString(entry.getKey(), entry.getValue());
       }
   
       SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
       String mesg = payloadData.get("_msg");
       String title = payloadData.get("title");
       String url = payloadData.get("url");
       String messageId = payloadData.get("_mId");
       String deliveryId = payloadData.get("_dId");
       YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
     }
   }
   ```

   ```
   public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
       if( message == null ) message = "No Content";
       if( title == null )   title = "No title";
       if( url == null )     url = "https://www.tripadvisor.fr";
       int iconId = R.drawable.notif_neotrip;
   
       // notify Neolane that a notification just arrived
       NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
       nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
         public void onNeolaneException(NeolaneException arg0, Object arg1) {}
         public void onIOException(IOException arg0, Object arg1) {}
         public void onComplete(String arg0, Object arg1){}
       });
       if (yourApplication.isActivityVisible())
       {
         Log.i("INFO", "The application has the focus" );
         ...
       }
       else
       {
         // notification creation :
         NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
         Notification notification;
   
         // Activity to start :
         Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
         notifIntent.putExtra("notificationText", message);
         notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
         notifIntent.putExtra("_dId", deliveryId);
         notifIntent.putExtra("_mId", messageId);
         notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
         PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
   
         notification = new Notification.Builder(context)
                 .setContentTitle(title)
                 .setContentText(message)
                 .setSmallIcon(iconId)
                 .setContentIntent(contentIntent)
                 .build();
   
         // launch the notification :
         notification.flags |= Notification.FLAG_AUTO_CANCEL;
         notificationManager.notify(Integer.valueOf(messageId), notification);
       }
   }
   ```

   다음은 열린 알림 추적을 위한 구현 예입니다(SDK의 notifyOpening **함수를 호출하여** 실행됨). NotificationActivity **클래스는** 이전 예제에서 **notifIntent** 개체를 만드는 데 사용되는 클래스에 해당합니다.

   ```
   public class NotificationActivity extends Activity {
    public static final String NOTIFICATION_URL_KEYNAME = "NotificationUrl";
    .....
    public void onCreate(Bundle savedBundle) {
     super.onCreate(savedBundle);
     setContentView(R.layout.notification_viewer);  
     .....  
     Bundle extra = getIntent().getExtras();  
     .....  
     //get the messageId and the deliveryId to do the tracking  
     String deliveryId = extra.getString("_dId");
     String messageId = extra.getString("_mId");
     if (deliveryId != null && messageId != null) {
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      neolaneAs.notifyOpening(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
       public void onNeolaneException(NeolaneException arg0, Object arg1) {}
       public void onIOException(IOException arg0, Object arg1) {}
       public void onComplete(String arg0, Object arg1) {}
       });
     }
    }
   }
   ```

* **iOS에서**:

   추적 기능을 사용하면 알림이 활성화되는 시간(열기)을 추적할 수 있습니다.

   ```
   (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
   fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
   {
   if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
   *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
   ...  
   completionHandler(UIBackgroundFetchResultNoData);
   }
   ```

   >[!NOTE]
   >
   >버전 7.0에서 **application:didReceiveRemoteNotification:fetchCompletionHandler** 함수가 구현되면 운영 체제에서 이 함수를 호출합니다. 따라서 **application:didReceiveRemoteNotification** 함수가 호출되지 않습니다.

## 자동 알림 추적 {#silent-notification-tracking}

iOS를 사용하면 자동 알림, 알림 또는 데이터를 전송하여 표시하지 않고 모바일 애플리케이션으로 바로 전송할 수 있습니다. Adobe Campaign을 통해 추적할 수 있습니다.

자동 알림을 추적하려면 아래 예를 따르십시오.

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

### RegisterDeviceStatus 위임 {#registerdevicestatus-delegate}

>[!NOTE]
>
>iOS에서만 사용할 수 있습니다.

iOS에서 위임 프로토콜을 사용하면 **registerDevice** 호출 결과를 얻을 수 있으며 등록 중 오류가 발생했는지 여부를 확인하는 데 사용할 수 있습니다.

registerDeviceStatus **프로토타입은** 다음과 같습니다.

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**상태를** 사용하면 등록에 성공했는지 또는 오류가 발생했는지 알 수 있습니다.

**ErrorReason** 은 발생한 오류에 대한 자세한 정보를 제공합니다. 사용 가능한 오류 및 설명에 대한 자세한 내용은 아래 표를 참조하십시오.

<table> 
 <thead>
  <tr>
   <th> 상태<br /> </th>
   <th> 설명<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCReisterDeviceStatusSuccess <br /> </td>
   <td> 등록 성공<br /> </td>
   <td> 비어 있음<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> ACC 마케팅 서버 호스트 이름이 비어 있거나 설정되지 않았습니다.<br /> </td>
   <td> 비어 있음<br /> </td>
  </tr>
  <tr> 
   <td> ACCReisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> 통합 키가 비어 있거나 설정되지 않았습니다.<br /> </td>
   <td> 비어 있음<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> ACC 연결 문제<br /> </td>
   <td> 자세한 정보(OS 현재 언어)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> 제공된 UUID(통합 키)를 알 수 없습니다.<br /> </td>
   <td> 비어 있음<br /> </td>
  </tr>
  <tr> 
   <td> ACCReisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> ACC 서버에 예기치 않은 오류가 반환되었습니다.<br /> </td>
   <td> ACC에 오류 메시지가 반환되었습니다.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** 프로토콜 및 **registerDeviceStatus** 위임 정의는 다음과 같습니다.

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

registerDeviceStatus **위임을 구현하려면** 다음 단계를 따르십시오.

1. SDK **초기화** 중에 setDelegate를 구현합니다.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. 클래스의 **@interface** 에 프로토콜을 추가합니다.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. AppDelegate에서 위임 **구현**.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

## 변수 {#variables}

이 변수를 사용하면 알림을 받은 후 모바일 애플리케이션 동작을 정의할 수 있습니다. 이러한 변수는 모바일 애플리케이션 코드와 Adobe Campaign 콘솔의 전용 모바일 애플리케이션 서비스 **[!UICONTROL Variables]** 탭에서 정의해야 합니다(Adobe Campaign [에서 모바일 애플리케이션 구성 참조](../../delivery/using/configuring-the-mobile-application.md)). 다음은 모바일 애플리케이션에서 알림의 추가된 변수를 수집할 수 있도록 하는 코드의 예입니다. 이 예에서는 &quot;VAR 파섹&quot; 변수를 사용합니다.

* **Android**:

   ```
   public void onReceive(Context context, Intent intent) {
        ...
       String event = intent.getStringExtra("VAR");
        ...
   }
   ```

* **iOS에서**:

   ```
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
       ....
       if( launchOptions )
       {
           // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
           NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
           if( localLaunchOptions )
           {
            ...
            [localLaunchOptions objectForKey:@"VAR"];
           ...
           }
      }
   }
   
   // Callback called when the application is already launched (whether the application is running foreground or background)
   - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
   {
       if( launchOptions )
       {
        ...
           [launchOptions objectForKey:@"VAR"];
       }
   }
   ```

>[!CAUTION]
>
>iOS 및 Android의 경우 알림 크기가 4kB로 제한되므로 짧은 변수 이름을 선택하는 것이 좋습니다.

## 알림 서비스 확장 {#notification-service-extension}

**iOS용**

미디어는 알림 서비스 확장 수준에서 다운로드해야 합니다.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

## 알림 컨텐츠 확장 {#notification-content-extension}

**iOS용**

이 수준에서는 다음을 수행해야 합니다.

* 컨텐츠 확장을 Adobe Campaign에서 보낸 카테고리에 연결합니다.

   모바일 응용 프로그램에서 이미지를 표시하려면 Adobe Campaign 및 모바일 응용 프로그램에서 카테고리 값을 &quot;image&quot;로 설정할 수 있습니다. UNotificationExtensionCategory **매개 변수를 &quot;image&quot;로** 설정하여 알림 확장을 만듭니다. 장치에서 푸시 알림을 받으면 정의된 카테고리 값에 따라 확장이 호출됩니다.

* 알림 레이아웃 정의

   관련 위젯을 사용하여 레이아웃을 정의해야 합니다. 이미지의 경우 위젯의 이름은 UIImageView **입니다**.

* 미디어 표시

   미디어 데이터를 위젯에 피드하려면 코드를 추가해야 합니다. 다음은 이미지에 대한 코드의 예입니다.

   ```
   #import "NotificationViewController.h"
   #import <UserNotifications/UserNotifications.h>
   #import <UserNotificationsUI/UserNotificationsUI.h>
   
   @interface NotificationViewController () <UNNotificationContentExtension>
   
   @property (strong, nonatomic) IBOutlet UIImageView *imageView;
   @property (strong, nonatomic) IBOutlet UILabel *notifContent;
   @property (strong, nonatomic) IBOutlet UILabel *label;
   
   @end
   
   @implementation NotificationViewController
   
   - (void)viewDidLoad {
       [super viewDidLoad];
       // Do any required interface initialization here.
   }
   
   - (void)didReceiveNotification:(UNNotification *)notification {
       self.label.text = notification.request.content.title;
       self.notifContent.text = notification.request.content.body;
       UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
       if ([attachment.URL startAccessingSecurityScopedResource])
       {
         NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
         self.imageView.image =[UIImage imageWithData: imageData];
         [attachment.URL stopAccessingSecurityScopedResource];
       }
   }
   @end
   ```
