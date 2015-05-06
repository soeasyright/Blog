title: "Push Notification"
date: 2015-04-12 02:52:17
tags: [iOS Notification,iOS EZCode]
categories: [iOS,EZCode]
---


```
//Set Notification
if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 8.0)
{
    [[UIApplication sharedApplication] registerUserNotificationSettings:[UIUserNotificationSettings 
     settingsForTypes:(UIUserNotificationTypeSound | UIUserNotificationTypeAlert | UIUserNotificationTypeBadge)      
categories:nil]];
    [[UIApplication sharedApplication] registerForRemoteNotifications];
}
else
{
    [[UIApplication sharedApplication] registerForRemoteNotificationTypes:
     (UIUserNotificationTypeBadge | UIUserNotificationTypeSound | UIUserNotificationTypeAlert)];
}
```

```
//Check currentUserNotificationSettings
UIRemoteNotificationType types;
if ([[[UIDevice currentDevice] systemVersion] floatValue] >= 8.0)
    types = [[UIApplication sharedApplication] currentUserNotificationSettings].types;
else
    types = [[UIApplication sharedApplication] enabledRemoteNotificationTypes];

return (types &amp; UIRemoteNotificationTypeAlert);
```
[ref_fb][]
[ref_fb]:https://www.facebook.com/groups/iostw/permalink/907809499246400/
