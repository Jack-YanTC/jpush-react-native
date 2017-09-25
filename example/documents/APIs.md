[中文文档](./APIs_zh.md)

- - [Common API:](#Common API)
  - [getRegistrationID](#getRegistrationID)
  - [setAlias](#setAlias)
  - [addTags](#addTags)
  - [setTags](#setTags)
  - [cleanTags](#cleanTags)
  - [setAlias](#setAlias)
  - [Open Notification Event](#Open Notification Event)
  - [Receive Notification event](#Receive Notification Event)
  - [Receive Custom Message Event](#Receive Custom Message Event)
- [iOS Only API:](#iOS Only API)
  - [setBadge](#setBadge)
  - [getBadge](#getBadge)
  - [setLocalNotification](#setLocalNotification)
  - [Open Notification Launch App Event](#Open Notification Launch App Event)
  - [Network Did Login Event](#Network Did Login Event)
- [Android Only API:](Android Only API)
  - ​

Note: In Android, you must call initPush first, iOS doesn't need.

### Common API

Common API for Android and iOS.
#### getRegistrationID

registrationId generated by JPush SDK according to deviceToken .

- getRegistrationID(function)

  ```javascript
  JPushModule.getRegistrationID((registrationId) => {})
  ```

#### setAlias

set device's application alias, you can push notificaiton with alias, every device can only have one alias.

- setAlias(alias, successCallback)

  ```javascript
  JPushModule.setAlias('alias', (success) => {})
  ```

#### addTags

use `addTags` to tag device , and can add many tag for you device, you can push remote notification with tag.

- addTags(tags, callback)

  ```javascript
  JPushModule.addTags(['tag1', 'tag2'], (success) => {})
  ```

#### deleteTags

- deleteTags(tags, callback)

  ```javascript
  JPushModule.deleteTags(['tag1', 'tag2'], (success) => {})
  ```

#### setTags

reset  tags. 

- setTags(tags, successCallback)

  ```javascript
  JPushModule.setTags(['tag1','tag2'], (success) => {})
  ```


#### cleanTags

- cleanTags(callback)

  ```javascript
  JPushModule.cleanTags((success) => {})
  ```

#### Open Notification Event

**NOTE: ** iOS need update to jpush-react-native@2.0.0+

- addReceiveOpenNotificationListener(function)  

  ```javascript
  var callback = (map) => {
      }
  JPushModule.addReceiveOpenNotificationListener(callback);
  ```

- removeReceiveOpenNotificationListener(function)
  ```javascript
  JPushModule.removeReceiveOpenNotificationListener(callback)
  ```

#### Receive Notification Event
**NOTE: ** iOS need update to jpush-react-native@2.0.0+

- addReceiveNotificationListener(function) 

  ```javascript
  var callback = (event) => {
        console.log("alertContent: " + JSON.stringify(event));

  }
  JPushModule.addReceiveNotificationListener(callback);
  ```

- removeReceiveNotificationListener(function)  

  ```
  JPushModule.removeReceiveNotificationListener(callback);
  ```


#### Receive Custom Message Event
**receive custom message**(Add this listener to receive custom message.)
**NOTE: ** iOS need update to jpush-react-native@2.0.0+
- addReceiveCustomMsgListener(function)  

  ```javascript
  var callback = (message) => {
        console.log("alertContent: " + JSON.stringify(message));

  }
  JPushModule.addReceiveCustomMsgListener(callback);
  ```


- removeReceiveCustomMsgListener(function)

  ```
  JPushModule.removeReceiveCustomMsgListener(callback);
  ```




### iOS Only API

All apis can find in jpush-react-native/index.js.

#### setBadge

set application's badge.

```js
  JPushModule.setBadge(5, (success) => {
    console.log(success)
  });
```

#### getBadge

get application's  badge.

```javascript
  JPushModule.getBadge((badge) => {
    console.log(badge)
  });
```

#### setLocalNotification

```javascript
setLocalNotification(  Date,    		// date  local notification fire data
                       textContain,     // String local notification content
                       badge,           // int   after local notification fire will set application badge
                       alertAction,     // String alert notification button content
                       notificationKey, // String set local notification identify
                       userInfo,   		// Object notification extra key-value
                       soundName   		// String custom sound，set it to null will use defoult sound
         )
```

```javascript
  JPushModule.setLocalNotification( this.state.date, 
                                    this.state.textContain,
                                    5, 
                                    'Action',
                                    'notificationIdentify',
                                    {myInfo: ""},
                                    null);
```

#### Open Notification Launch App Event

**NOTE: ** iOS need update to jpush-react-native@2.0.0+

- addOpenNotificationLaunchAppListener(function) 

  add listener：application not running and tap notification to run application, will fire callback added by`addOpenNotificationLaunchAppListener` .

  ```javascript
  var callback = (notification) => {
  	console.log(JSON.stringify(nofitifation))
    }
  JPushModule.addOpenNotificationLaunchAppListener(callback)
  ```

- removeOpenNotificationLaunchAppListener(function)

  ```javascript
  JPushModule.removeOpenNotificationLaunchAppListener(callback)
  ```

  remove listener：application not running and tap notification to run application，`removeOpenNotificationLaunchAppListener` and `addOpenNotificationLaunchAppListener` used in pairs.

**Network Did Login Event**

**NOTE: ** iOS need update to jpush-react-native@2.0.0+

- addnetworkDidLoginListener(function)

  add listener: JPush SDK did login event ，`setTag` and `setAlias` needs to be called after network did login Event. 

  ```javascript
  var callback = () => {
    }
  JPushModule.addnetworkDidLoginListener(callback)
  ```

- removenetworkDidLoginListener(function)

  remove: JPush SDK did login event ，`removenetworkDidLoginListener` and `addnetworkDidLoginListener` used in pairs.



### Android Only API