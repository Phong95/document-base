---
sidebar_position: 6
---
# Hệ thống thông báo
Ứng dụng triển khai hệ thống thông báo từ firbase cloud messaging và notifee.
Sau khi triển khai 2 hệ thống thông báo trên, sau đó import vào NotificationHub để sử dụng chung cho toàn bộ dự án.
```
notifications
├── FirebaseNotification.ts
├── NotifeeNotification.ts
└── NotificationHub.ts
```

## Trước khi bắt đầu
Cài đặt các yêu cầu theo hướng dẫn sau:
- [React Native Firebase Cloud Messaging](https://rnfirebase.io/messaging/usage)
- [Notifee](https://notifee.app/)

:::tip
Có thể thay thế firebase cloud messaging bằng [OneSignal](https://onesignal.com/). 
:::

## FirebaseNotification

``` typescript
import messaging, { firebase } from '@react-native-firebase/messaging';
import AsyncStorage from '@react-native-async-storage/async-storage';
import { onDisplayNotification } from './NotifeeNotification';
import { MobileAppNotification } from '../model/notification/MobileAppNotification';
import { NavigationContainerRef } from '../navigation/GlobalNavigationContainer';
import { Store } from '../redux/store/Store';
import { SET_NOTIFICATION_REPORT, SetNotificationReport } from '../redux/actions/ReportAction2';
import appScenario from '../scenario/AppScenario';

export const RequestUserPermission = async () => {
  const authStatus = await messaging().requestPermission();
  const enabled =
    authStatus === messaging.AuthorizationStatus.AUTHORIZED ||
    authStatus === messaging.AuthorizationStatus.PROVISIONAL;

  if (enabled) {
    console.log('Authorization status:', authStatus);
    await GetFCMToken();
  }
};

async function GetFCMToken() {
  let fcmToken = await AsyncStorage.getItem('fcmToken');
  console.log(fcmToken, 'old token');
  if (!fcmToken) {
    try {
      await firebase.messaging().requestPermission();
      const fcmToken = await messaging().getToken();
      if (fcmToken) {
        console.log(fcmToken, 'new token');
        await AsyncStorage.setItem('fcmToken', fcmToken);
      }
    } catch (error) {
      console.log(error, 'error in fcmToken');
    }
  }

}

export async function SubscribeToTopic(topicName: string) {
  let topics: string[] | null = null;
  let object = await AsyncStorage.getItem('fcmTopics');
  if (!topics) topics = [];
  if (!topics.includes(topicName)) topics.push(topicName);
  await AsyncStorage.setItem('fcmTopics', JSON.stringify(topics));
  messaging()
    .subscribeToTopic(topicName)
    .then(() => console.log('Subscribed to topic: ', topicName));
}
export async function UnSubscribeToTopic(topicName: string) {
  messaging()
    .unsubscribeFromTopic(topicName)
    .then(() => console.log('UnSubscribed to topic: ', topicName));
}
export async function UnSubscribeAllTopic() {
  let topics: string[] | null = null;
  let object = await AsyncStorage.getItem('fcmTopics');

}
export const NotificationListener = (callBackIfOpenNotification = (data: any) => { }) => {
  // Register background handler
  messaging().setBackgroundMessageHandler(async (remoteMessage: any) => {
    console.log('Message handled in the background!', remoteMessage);

  });

  messaging().onNotificationOpenedApp((remoteMessage: any) => {
    console.log(
      'Notification caused app to open from background state:',
      remoteMessage,
    );
    if (remoteMessage.data) {
      Store.dispatch({ type: SET_NOTIFICATION_REPORT, payload: remoteMessage.data })
    }
  });

  messaging()
    .getInitialNotification()
    .then((remoteMessage: any) => {
      if (remoteMessage) {
        console.log(
          'Notification caused app to open from quit state:',
          remoteMessage,
        );
        if (remoteMessage.data) {
            Store.dispatch({ type: SET_NOTIFICATION_REPORT, payload: remoteMessage.data })

        }
      }
    });

  messaging().onMessage(async (remoteMessage: any) => {
    console.log('notification on foreground state....', remoteMessage);
    if (remoteMessage && remoteMessage.notification) {
      onDisplayNotification(remoteMessage);
    }
  });

};

```

## NotifeeNotification

``` typescript
import notifee, {
  AndroidImportance,
  AndroidLaunchActivityFlag,
} from '@notifee/react-native';
import { Store } from '../redux/store/Store';
import { SET_NOTIFICATION_REPORT } from '../redux/actions/ReportAction2';

export interface INotification {
  title: string;
  body: string;
}
export const NotifeeOnBackground = () => {
  notifee.onBackgroundEvent(async ({type, detail}) => {
    console.log('Notifeeeeeeeeeeeee On Background', detail);
    if(detail?.notification?.data)
    {
      Store.dispatch({ type: SET_NOTIFICATION_REPORT, payload: detail?.notification?.data })
    }
  });
};
export const CreateAndroidChannel = async () => {
  // Create a channel (required for Android)
  const channelId = await notifee.createChannel({
    id: 'default',
    name: 'Default Channel',
    importance: AndroidImportance.HIGH,
  });
};

export const onDisplayNotification = async (data: any) => {
  if (data) {
    // Request permissions (required for iOS)
    await notifee.requestPermission();
    let channel = await notifee.getChannel('default');
    if (!channel) {
      await CreateAndroidChannel();
    }
    // Display a notification
    await notifee.displayNotification({
      title: data.notification.title,
      body: data.notification.body,
      android: {
        channelId: 'default',
        pressAction: {
          id: 'default',
          launchActivity: 'default',
          launchActivityFlags: [AndroidLaunchActivityFlag.SINGLE_TOP],
        },
      },
      data: data.data,
    });
  }
};

```

## NotificationHub

``` typescript
import { NavigationContainerRef } from "../navigation/GlobalNavigationContainer";
import { NotificationListener, RequestUserPermission } from "./FirebaseNotification";
import { CreateAndroidChannel, NotifeeOnBackground } from "./NotifeeNotification";

export async function NotificationRegister() {
    let ref = NavigationContainerRef;
    await NotificationListener();
    await RequestUserPermission();
    await CreateAndroidChannel();
    await NotifeeOnBackground();
}
```

## Triển khai
trong file `index.js`, import từ `NotificationHub.ts`

``` javascript
import {AppRegistry} from 'react-native';
import {name as appName} from './app.json';
import App, {AppWrapper} from './App';
import {
    NotificationRegister,
  } from './src/notifications/NotificationHub';
import { NavigationContainerRef } from './src/navigation/GlobalNavigationContainer';

NotificationRegister(NavigationContainerRef);
AppRegistry.registerComponent(appName, () => AppWrapper);
```