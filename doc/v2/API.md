## [1 Prepaid package](#11-listsubscriberprepaidpackages)

[1.1 listSubscriberPrepaidPackages](#11-listsubscriberprepaidpackages)

## [Error codes](#error-codes)

# 1. Prepaid package
## 1.1 listSubscriberPrepaidPackages

### Description
This request can be used to list all the pre paid packages of a subscriber (if any).

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### Outputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|listSubscriberPrepaidPackages.callUseSingleCounter|Mandatory|Indicates if MOC and MTC are charged on the same counter.</br>If the flag is false MOC seconds are charged on `usedmocsecond` and the limit is `pckmocsecond`. While the MTC seconds are charged on `usedmtcsecond` and the limit is `pckmtcsecond`.</br>If the flag is true, no difference is made between MOC and MTC, they both are considered as calls charged on the same counter with the same limit. Both MOC and MTC seconds are charged on `usedmocsecond` counter. The limit for both MOC and MTC is `pckmocsecond`.|
|listSubscriberPrepaidPackages.packages|Mandatory|Array that contains all the subscriber prepaid packages (recurring and regular), see `Subscriber prepaid package` in [OcsObjects.md](../v1/OcsObjects.md). If the subscriber doesn't have any prepaid package, this array will be empty.|
|listSubscriberPrepaidPackages.recurring|Mandatory|Array that contains all the recurring packages (still active and inactive) of the subscriber. You can find all the packages (from `packages` array) created for a recurring packages with `recurringPackage` field of the prepaid package.|


### 1.1.1 By subscriber ID
#### Request
```json
{
  "listSubscriberPrepaidPackages" : {
    "subscriberId" : 1000
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberPrepaidPackages" : {
    "packages" : [ {
      "rdbDestinationZones" : {
        "destinationzoneid" : 5,
        "destinationzonename" : "Denis Destination list"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 2214,
        "prepaidpackagetemplatename" : "Denis Italy"
      },
      "subscriberprepaidpackageid" : 1007,
      "subscriberid" : 4,
      "priority" : 3,
      "locationzoneid" : 27,
      "destinationzoneid" : 5,
      "pckdatabyte" : 104857600,
      "pckmocsecond" : 0,
      "pckmtcsecond" : 0,
      "pckmosmsnumber" : 0,
      "pckmtsmsnumber" : 0,
      "tsassigned" : "2023-08-01T13:25:08",
      "tsactivationutc" : "2023-09-21T14:49:47",
      "tsexpirationutc" : "2023-10-01T14:49:47",
      "useddatabyte" : 104857600,
      "usedmocsecond" : 0,
      "usedmocvoipsecond" : 0,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 10,
      "cost" : 9.99,
      "templateId" : 2214,
      "esimId" : 64612,
      "active" : true
    }, {
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 9280,
        "prepaidpackagetemplatename" : "PDEL Recurring"
      },
      "subscriberprepaidpackageid" : 1039,
      "subscriberid" : 4,
      "priority" : 4,
      "locationzoneid" : 27,
      "pckdatabyte" : 0,
      "pckmocsecond" : 0,
      "pckmtcsecond" : 0,
      "pckmosmsnumber" : 0,
      "pckmtsmsnumber" : 0,
      "tsassigned" : "2023-10-02T08:25:03",
      "tsactivationutc" : "2023-10-02T08:00:00",
      "tsexpirationutc" : "2023-11-16T08:00:00",
      "useddatabyte" : 0,
      "usedmocsecond" : 0,
      "usedmocvoipsecond" : 0,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 45,
      "cost" : 123.0,
      "templateId" : 9280,
      "esimId" : 64612,
      "active" : true,
      "recurringPackage" : 1
    }, {
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 9280,
        "prepaidpackagetemplatename" : "PDEL Recurring"
      },
      "subscriberprepaidpackageid" : 1040,
      "subscriberid" : 4,
      "priority" : 5,
      "locationzoneid" : 27,
      "pckdatabyte" : 1073741824,
      "pckmocsecond" : 1,
      "pckmtcsecond" : 2,
      "pckmosmsnumber" : 3,
      "pckmtsmsnumber" : 4,
      "tsassigned" : "2023-10-02T09:07:35",
      "tsactivationutc" : "2023-10-02T13:50:00",
      "tsexpirationutc" : "2023-11-16T13:50:00",
      "useddatabyte" : 0,
      "usedmocsecond" : 0,
      "usedmocvoipsecond" : 0,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 45,
      "cost" : 123.0,
      "templateId" : 9280,
      "esimId" : 64612,
      "active" : true,
      "recurringPackage" : 3
    }, {
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 9280,
        "prepaidpackagetemplatename" : "PDEL Recurring"
      },
      "subscriberprepaidpackageid" : 1041,
      "subscriberid" : 4,
      "priority" : 6,
      "locationzoneid" : 27,
      "pckdatabyte" : 1073741824,
      "pckmocsecond" : 1,
      "pckmtcsecond" : 2,
      "pckmosmsnumber" : 3,
      "pckmtsmsnumber" : 4,
      "tsassigned" : "2023-10-02T09:14:37",
      "tsactivationutc" : "2023-10-02T13:50:00",
      "tsexpirationutc" : "2023-11-02T13:50:00",
      "useddatabyte" : 0,
      "usedmocsecond" : 0,
      "usedmocvoipsecond" : 0,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 45,
      "cost" : 123.0,
      "templateId" : 9280,
      "esimId" : 64612,
      "active" : true,
      "recurringPackage" : 4
    }, {
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 9280,
        "prepaidpackagetemplatename" : "PDEL Recurring"
      },
      "subscriberprepaidpackageid" : 1042,
      "subscriberid" : 4,
      "priority" : 7,
      "locationzoneid" : 27,
      "pckdatabyte" : 1073741824,
      "pckmocsecond" : 1,
      "pckmtcsecond" : 2,
      "pckmosmsnumber" : 3,
      "pckmtsmsnumber" : 4,
      "tsassigned" : "2023-10-02T09:31:21",
      "tsactivationutc" : "2023-10-02T09:31:21",
      "tsexpirationutc" : "2023-11-02T09:31:21",
      "useddatabyte" : 0,
      "usedmocsecond" : 0,
      "usedmocvoipsecond" : 0,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 45,
      "cost" : 123.0,
      "templateId" : 9280,
      "esimId" : 64612,
      "active" : true,
      "recurringPackage" : 5
    } ],
    "recurring" : [ {
      "id" : 1,
      "startTimeUTC" : "2023-10-02T08:00:00",
      "lastPackageCreationTimeUTC" : "2023-10-02T08:25:03",
      "template" : 9280,
      "templateName" : "Template XYZ",
      "subscriber" : 4,
      "nbOccurrence" : 10,
      "nbCreated" : 1,
      "recurringPeriodicityType" : 1,
      "recurringPeriodicityFrequency" : 7,
      "reportUnitsPreviousPackage" : true,
      "active" : true
    }, {
      "id" : 2,
      "startTimeUTC" : "2023-10-02T23:50:00",
      "template" : 9280,
      "templateName" : "Template XYZ",
      "subscriber" : 4,
      "nbOccurrence" : 10,
      "nbCreated" : 0,
      "recurringPeriodicityType" : 1,
      "recurringPeriodicityFrequency" : 7,
      "reportUnitsPreviousPackage" : true,
      "active" : true
    }, {
      "id" : 3,
      "startTimeUTC" : "2023-10-02T13:50:00",
      "lastPackageCreationTimeUTC" : "2023-10-02T09:07:35",
      "template" : 9280,
      "templateName" : "Template XYZ",
      "subscriber" : 4,
      "nbOccurrence" : 10,
      "nbCreated" : 1,
      "recurringPeriodicityType" : 1,
      "recurringPeriodicityFrequency" : 7,
      "reportUnitsPreviousPackage" : true,
      "active" : false
    }, {
      "id" : 4,
      "startTimeUTC" : "2023-10-02T13:50:00",
      "lastPackageCreationTimeUTC" : "2023-10-02T09:14:37",
      "template" : 9280,
      "templateName" : "Template XYZ",
      "subscriber" : 4,
      "nbCreated" : 1,
      "recurringPeriodicityType" : 2,
      "recurringPeriodicityFrequency" : 1,
      "reportUnitsPreviousPackage" : true,
      "active" : true
    }, {
      "id" : 5,
      "startTimeUTC" : "2023-10-02T09:31:21",
      "lastPackageCreationTimeUTC" : "2023-10-02T09:31:21",
      "template" : 9280,
      "templateName" : "Template XYZ",
      "subscriber" : 4,
      "nbOccurrence" : 10,
      "nbCreated" : 1,
      "recurringPeriodicityType" : 2,
      "recurringPeriodicityFrequency" : 1,
      "reportUnitsPreviousPackage" : true,
      "active" : true
    } ],
    "callUseSingleCounter" : true
  }
}
```
#### Remark(s)

- If `recurringPackage` is present in a prepaid package, the package is a recurring one. It contains a reference to the recurring package (in `packages` array). To find all the prepaid package of a specific recurring package, list from `packages` the prepaid package with `recurringPackage` equals to recurring package `id`


### 1.1.2 By IMSI
#### Request
```json
{
  "listSubscriberPrepaidPackages" : {
    "imsi" : "12345678901234"
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberPrepaidPackages" : {
    "callUseSingleCounter" : false
  }
}
```
#### Remark(s)

- Same content as previous request


### 1.1.3 By ICCID
#### Request
```json
{
  "listSubscriberPrepaidPackages" : {
    "iccid" : "123456789012345678"
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberPrepaidPackages" : {
    "callUseSingleCounter" : false
  }
}
```
#### Remark(s)

- Same content as previous request


### 1.1.4 By MSISDN
#### Request
```json
{
  "listSubscriberPrepaidPackages" : {
    "msisdn" : "123456789123"
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberPrepaidPackages" : {
    "callUseSingleCounter" : false
  }
}
```
#### Remark(s)

- Same content as previous request


### 1.1.5 By multi imsi
#### Request
```json
{
  "listSubscriberPrepaidPackages" : {
    "multiImsi" : "12345678901234"
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberPrepaidPackages" : {
    "callUseSingleCounter" : false
  }
}
```
#### Remark(s)

- Same content as previous request


### 1.1.6 By Activation code
#### Request
```json
{
  "listSubscriberPrepaidPackages" : {
    "activationCode" : "Activation code"
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberPrepaidPackages" : {
    "callUseSingleCounter" : false
  }
}
```
#### Remark(s)

- Same content as previous request


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


# Error codes
| Code | Description |
|------|---|
| 0 | OK |
| 1 | UNKNOWN_REQUEST |
| 2 | INVALID_REQUEST |
| 3 | UNEXPECTED_ERROR |
| 4 | DB_DUPLICATE_ENTRY |
| 5 | DB_DATA_INCONSISTENCY |
| 6 | DB_NOT_FOUND |
| 7 | DB_ERROR |
| 8 | NO_API_ACCOUNT_FOR_RESELLER |
| 9 | SRC_IP_NOT_AUTHORISED |
| 10 | INVALID_RESELLER |
| 11 | RESOURCE_NOT_VISIBLE |
| 12 | RESOURCE_READ_ONLY |
| 13 | SMS_API_ERROR |
| 14 | OPERATION_IMPOSSIBLE |
| 15 | HLR_API_ERROR |
| 16 | STEERING_API_ERROR |
| 100 | TRAFFIC_CONTROL_LIMIT_EXCEEDED |

