# Notification answer
When receiving any type of notification, the following answer is expected from the customer that received the notification:
```json
{
  "result":{
    "code":0,
    "msg":"OK"
  }
}
```

In case the notification has processed correctly, the `result.code` must be `0`, with `result.msg` = `OK`.
In case of error, the customer can return any `result.code` > 0, with appropriate `result.msg`. The error
will store in our logs and will help debug in case of issue.


# Prepaid package usage
## Description
This notification is configured in the `Reseller` object with two thresholds, expressed in percentage. When
the subscriber consumption on a specific prepaid package crossed one of the two thresholds, this notification is sent
to the URL configured in the notification.

Here is an example of configuration:

![reseller_package_notif.png](pics%2Freseller_package_notif.png)

## Notification content
The HTTP request received by the customer will contain a JSON object with the following attributes:

| Attribute           | Presence | Description                                                      |
|---------------------|----------|------------------------------------------------------------------|
| unitsBefore         | MAND.    | Units present on the package before the usage.                   |
| unitsAfter          | MAND.    | Units present on the package after the usage.                    |
| thresholdPercentage | MAND.    | The thresholds that has been crossed, in percentage.             |
| thresholdUnits      | MAND.    | The thresholds that has been crossed, in units.                  |
| subscriberPackageId | MAND.    | The id of the prepaid package of the subscriber.                 |
| totalUnits          | MAND.    | Maximum units the subscriber can consume on the prepaid package. |
| subscriberId        | MAND.    | The id of the subscriber.                                        |
| subscriberIMSI      | MAND.    | The IMSI of the subscriber.                                      |
| usageType           | MAND.    | The usage type: `MOC` or `MTC` or `MO_SMS`,`MT_SMS`,`DATA`.      |

Here is an example of notification:

```json
{
  "subscriberPrepaidPackage": {
    "unitsBefore": 1000000,
    "unitsAfter": 2000000,
    "thresholdPercentage": "80",
    "thresholdUnits": "1500000",
    "subscriberPackageId": 123,
    "totalUnits": 2300000,
    "subscriberId": 123,
    "subscriberIMSI": "123456789",
    "usageType": "DATA"
  }
}
```


# ES2+ Notification
## Description
This notification is configured in the `Reseller` object with an URL where we will send the notification to the customer.
Each time we receive a status update of an eSIM configured in our system, we are checking if the customer has configured
an "ES2+ Notification". In such a case, the new status of the eSIM is sent to the customer.

Here is an example of configuration:  
![reseller_ES2_notif.png](pics%2Freseller_ES2_notif.png)


The HTTP request received by the customer will contain a JSON object with the following attributes:

| Attribute | Presence | Description                                                        |
|-----------|----------|--------------------------------------------------------------------|
| iccid     | MAND.    | The ICCID of the subscriber.                                       |
| imsi      | MAND.    | The IMSI of the subscriber.                                        |
| eid       | MAND.    | The EID of the subscriber.                                           |
| subsId    | MAND.    | The internal ID of the subscriber that can be used in the OCS API. |
| status    | MAND.    | The new status of the eSIM if the subscriber.                      |

Here is an example of notification:

```json
{
  "iccid" : "12334567891234546",
  "imsi" : "123456789123456",
  "eid":"89049032004008882600007171733779",
  "subsId":4,
  "status" : "Enable"
}
```
