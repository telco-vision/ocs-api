## [1 Reseller](#11-listreselleraccount)

[1.1 listResellerAccount](#11-listreselleraccount)

## [2 Subscriber](#21-listsubscriber)

[2.1 listSubscriber](#21-listsubscriber)

[2.2 affectSubscriberRealPhoneNumber](#22-affectsubscriberrealphonenumber)

[2.3 affectSubscriberFakePhoneNumber](#23-affectsubscriberfakephonenumber)

## [3 Prepaid package](#31-listprepaidpackagetemplate)

[3.1 listPrepaidPackageTemplate](#31-listprepaidpackagetemplate)

[3.2 listLocationZoneElement](#32-listlocationzoneelement)

[3.3 affectPackageToSubscriber](#33-affectpackagetosubscriber)

## [4 Tariff](#41-listresellertariff)

[4.1 listResellerTariff](#41-listresellertariff)

[4.2 listSubscriberTariff](#42-listsubscribertariff)

[4.3 listTariffRule](#43-listtariffrule)

## [5 Statistics](#51-getsubscriberactiveperiod)

[5.1 getSubscriberActivePeriod](#51-getsubscriberactiveperiod)

[5.2 subscriberUsageOverPeriod](#52-subscriberusageoverperiod)

[5.3 subscriberNetworkEventsOverPeriod](#53-subscribernetworkeventsoverperiod)

## [6 SMS](#61-sendmtsms)

[6.1 sendMtSms](#61-sendmtsms)

## [Error codes](#error-codes)

# 1. Reseller
## 1.1 listResellerAccount

### Description
This request can be used to retrieve the list of accounts. You can retrieve the list of a specific reseller
or all accounts of all your reseller.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|resellerId|Optional|The ID of the reseller|


### 1.1.1 Account of all resellers
#### Request
```json
{
  "listResellerAccount" : { }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listResellerAccount" : {
    "reseller" : [ {
      "id" : 1,
      "name" : "Test Reseller",
      "account" : [ {
        "id" : 4,
        "name" : "Test - Second account",
        "balance" : 660.5500000000001
      }, {
        "id" : 7,
        "name" : "Test - Subs X",
        "balance" : 1000.0
      }, {
        "id" : 55,
        "name" : "FUT",
        "balance" : 70.06
      }, {
        "id" : 104,
        "name" : "test from UI",
        "balance" : 100.0
      }, {
        "id" : 125,
        "name" : "Denis new account",
        "balance" : 0.0
      } ]
    }, {
      "id" : 10,
      "name" : "Test Reseller 3",
      "account" : [ {
        "id" : 37,
        "name" : "TestSubscribers",
        "balance" : 97.80718309495325
      } ]
    }, {
      "id" : 58,
      "name" : "Reseller XYZ",
      "account" : [ {
        "id" : 118,
        "name" : "Test dev account name",
        "balance" : 100.0
      }, {
        "id" : 119,
        "name" : "Test dev account name 2",
        "balance" : 100.0
      } ]
    } ]
  }
}
```
### 1.1.2 Account of specific reseller
#### Request
```json
{
  "listResellerAccount" : {
    "resellerId" : 123
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
  "listResellerAccount" : {
    "reseller" : [ {
      "id" : 10,
      "name" : "Test Reseller 3",
      "account" : [ {
        "id" : 37,
        "name" : "TestSubscribers",
        "balance" : 97.80718309495325
      } ]
    } ]
  }
}
```
# 2. Subscriber
## 2.1 listSubscriber

### Description
This request can be used to search for subscriber. You can search for subscribers by:
- IMSI prefix
- ICCID prefix
- Account
- eSIM activation code


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|imsiPrefix|Optional|IMSI Prefix for the subscribers to list. Minimum 10 digits long|
|iccidPrefix|Optional|ICCID prefix for the subscribers to list. Minimum 13 digits long|
|accountId|Optional|The ID of the account. The request will return the list of all the subscriber attached to this account|
|activationCode|Optional|The eSIM activation code. The request will return the subscriber with the eSIM having this activation code|


### 2.1.1 IMSI prefix
#### Request
```json
{
  "listSubscriber" : {
    "imsiPrefix" : "9999900000"
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
  "listSubscriber" : {
    "subscriberList" : [ {
      "imsiList" : [ {
        "id" : 44974,
        "subscriberId" : 45046,
        "imsi" : "999990000002001",
        "startDate" : "2022-05-23T16:47:41",
        "iccid" : "9999900017170020010"
      } ],
      "phoneNumberList" : [ {
        "id" : 44932,
        "subscriberId" : 45046,
        "phoneNumber" : "32477002001",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "multiImsi" : [ {
        "id" : 44896,
        "subscriberId" : 45046,
        "imsi" : "999990000002001",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "status" : [ {
        "id" : 44893,
        "subscriberId" : 45046,
        "startDate" : "2022-05-23T16:47:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 45046,
        "esim" : true,
        "status" : "AFFECTED",
        "affectationDateUtc" : "2022-05-27T11:56:07",
        "pin1" : "6310",
        "puk1" : "89116899",
        "pin2" : "0569",
        "puk2" : "25380546",
        "smdpServer" : "some.server",
        "activationCode" : "some code",
        "confirmationCode" : "confirm code"
      },
      "subscriberId" : 45046,
      "batchId" : "Some_test_batch",
      "accountId" : 4,
      "resellerId" : 1,
      "prepaid" : true,
      "balance" : 150.0,
      "activationDate" : "2022-05-30T06:35:38",
      "email" : "andreas@telco-vision.com",
      "useAccountForCharging" : true,
      "allowedMoc" : false,
      "allowedMtc" : false,
      "allowedData" : true,
      "allowedMosms" : false,
      "allowedMtsms" : false,
      "account" : "Test - Second account",
      "reseller" : "Test Reseller"
    }, {
      "imsiList" : [ {
        "id" : 44977,
        "subscriberId" : 45049,
        "imsi" : "999990000002002",
        "startDate" : "2022-05-23T16:47:41",
        "iccid" : "9999900017170020028"
      } ],
      "phoneNumberList" : [ {
        "id" : 44935,
        "subscriberId" : 45049,
        "phoneNumber" : "32477002002",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "multiImsi" : [ {
        "id" : 44899,
        "subscriberId" : 45049,
        "imsi" : "999990000002002",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "status" : [ {
        "id" : 44896,
        "subscriberId" : 45049,
        "startDate" : "2022-05-23T16:47:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 45049,
        "esim" : true,
        "status" : "AFFECTED",
        "affectationDateUtc" : "2022-05-30T07:04:31",
        "pin1" : "4366",
        "puk1" : "51885819",
        "pin2" : "5919",
        "puk2" : "03208995",
        "smdpServer" : "some.server",
        "activationCode" : "some code1",
        "confirmationCode" : "confirm code"
      },
      "subscriberId" : 45049,
      "batchId" : "Some_test_batch",
      "accountId" : 4,
      "resellerId" : 1,
      "prepaid" : true,
      "balance" : 150.0,
      "activationDate" : "2022-05-30T07:04:31",
      "email" : "andreas@telco-vision.com",
      "useAccountForCharging" : true,
      "allowedMoc" : false,
      "allowedMtc" : false,
      "allowedData" : true,
      "allowedMosms" : false,
      "allowedMtsms" : false,
      "account" : "Test - Second account",
      "reseller" : "Test Reseller"
    } ],
    "hasMore" : false,
    "nbFound" : 11
  }
}
```
### 2.1.2 ICCID prefix
#### Request
```json
{
  "listSubscriber" : {
    "iccidPrefix" : "9999900017170"
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
  "listSubscriber" : {
    "subscriberList" : [ {
      "imsiList" : [ {
        "id" : 44974,
        "subscriberId" : 45046,
        "imsi" : "999990000002001",
        "startDate" : "2022-05-23T16:47:41",
        "iccid" : "9999900017170020010"
      } ],
      "phoneNumberList" : [ {
        "id" : 44932,
        "subscriberId" : 45046,
        "phoneNumber" : "32477002001",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "multiImsi" : [ {
        "id" : 44896,
        "subscriberId" : 45046,
        "imsi" : "999990000002001",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "status" : [ {
        "id" : 44893,
        "subscriberId" : 45046,
        "startDate" : "2022-05-23T16:47:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 45046,
        "esim" : true,
        "status" : "AFFECTED",
        "affectationDateUtc" : "2022-05-27T11:56:07",
        "pin1" : "6310",
        "puk1" : "89116899",
        "pin2" : "0569",
        "puk2" : "25380546",
        "smdpServer" : "some.server",
        "activationCode" : "some code",
        "confirmationCode" : "confirm code"
      },
      "subscriberId" : 45046,
      "batchId" : "Some_test_batch",
      "accountId" : 4,
      "resellerId" : 1,
      "prepaid" : true,
      "balance" : 150.0,
      "activationDate" : "2022-05-30T06:35:38",
      "email" : "andreas@telco-vision.com",
      "useAccountForCharging" : true,
      "allowedMoc" : false,
      "allowedMtc" : false,
      "allowedData" : true,
      "allowedMosms" : false,
      "allowedMtsms" : false,
      "account" : "Test - Second account",
      "reseller" : "Test Reseller"
    }, {
      "imsiList" : [ {
        "id" : 44977,
        "subscriberId" : 45049,
        "imsi" : "999990000002002",
        "startDate" : "2022-05-23T16:47:41",
        "iccid" : "9999900017170020028"
      } ],
      "phoneNumberList" : [ {
        "id" : 44935,
        "subscriberId" : 45049,
        "phoneNumber" : "32477002002",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "multiImsi" : [ {
        "id" : 44899,
        "subscriberId" : 45049,
        "imsi" : "999990000002002",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "status" : [ {
        "id" : 44896,
        "subscriberId" : 45049,
        "startDate" : "2022-05-23T16:47:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 45049,
        "esim" : true,
        "status" : "AFFECTED",
        "affectationDateUtc" : "2022-05-30T07:04:31",
        "pin1" : "4366",
        "puk1" : "51885819",
        "pin2" : "5919",
        "puk2" : "03208995",
        "smdpServer" : "some.server",
        "activationCode" : "some code1",
        "confirmationCode" : "confirm code"
      },
      "subscriberId" : 45049,
      "batchId" : "Some_test_batch",
      "accountId" : 4,
      "resellerId" : 1,
      "prepaid" : true,
      "balance" : 150.0,
      "activationDate" : "2022-05-30T07:04:31",
      "email" : "andreas@telco-vision.com",
      "useAccountForCharging" : true,
      "allowedMoc" : false,
      "allowedMtc" : false,
      "allowedData" : true,
      "allowedMosms" : false,
      "allowedMtsms" : false,
      "account" : "Test - Second account",
      "reseller" : "Test Reseller"
    } ],
    "hasMore" : false,
    "nbFound" : 11
  }
}
```
### 2.1.3 Account Id
#### Request
```json
{
  "listSubscriber" : {
    "accountId" : 4
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
  "listSubscriber" : {
    "subscriberList" : [ {
      "imsiList" : [ {
        "id" : 44974,
        "subscriberId" : 45046,
        "imsi" : "999990000002001",
        "startDate" : "2022-05-23T16:47:41",
        "iccid" : "9999900017170020010"
      } ],
      "phoneNumberList" : [ {
        "id" : 44932,
        "subscriberId" : 45046,
        "phoneNumber" : "32477002001",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "multiImsi" : [ {
        "id" : 44896,
        "subscriberId" : 45046,
        "imsi" : "999990000002001",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "status" : [ {
        "id" : 44893,
        "subscriberId" : 45046,
        "startDate" : "2022-05-23T16:47:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 45046,
        "esim" : true,
        "status" : "AFFECTED",
        "affectationDateUtc" : "2022-05-27T11:56:07",
        "pin1" : "6310",
        "puk1" : "89116899",
        "pin2" : "0569",
        "puk2" : "25380546",
        "smdpServer" : "some.server",
        "activationCode" : "some code",
        "confirmationCode" : "confirm code"
      },
      "subscriberId" : 45046,
      "batchId" : "Some_test_batch",
      "accountId" : 4,
      "resellerId" : 1,
      "prepaid" : true,
      "balance" : 150.0,
      "activationDate" : "2022-05-30T06:35:38",
      "email" : "andreas@telco-vision.com",
      "useAccountForCharging" : true,
      "allowedMoc" : false,
      "allowedMtc" : false,
      "allowedData" : true,
      "allowedMosms" : false,
      "allowedMtsms" : false,
      "account" : "Test - Second account",
      "reseller" : "Test Reseller"
    }, {
      "imsiList" : [ {
        "id" : 44977,
        "subscriberId" : 45049,
        "imsi" : "999990000002002",
        "startDate" : "2022-05-23T16:47:41",
        "iccid" : "9999900017170020028"
      } ],
      "phoneNumberList" : [ {
        "id" : 44935,
        "subscriberId" : 45049,
        "phoneNumber" : "32477002002",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "multiImsi" : [ {
        "id" : 44899,
        "subscriberId" : 45049,
        "imsi" : "999990000002002",
        "startDate" : "2022-05-23T16:47:41"
      } ],
      "status" : [ {
        "id" : 44896,
        "subscriberId" : 45049,
        "startDate" : "2022-05-23T16:47:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 45049,
        "esim" : true,
        "status" : "AFFECTED",
        "affectationDateUtc" : "2022-05-30T07:04:31",
        "pin1" : "4366",
        "puk1" : "51885819",
        "pin2" : "5919",
        "puk2" : "03208995",
        "smdpServer" : "some.server",
        "activationCode" : "some code1",
        "confirmationCode" : "confirm code"
      },
      "subscriberId" : 45049,
      "batchId" : "Some_test_batch",
      "accountId" : 4,
      "resellerId" : 1,
      "prepaid" : true,
      "balance" : 150.0,
      "activationDate" : "2022-05-30T07:04:31",
      "email" : "andreas@telco-vision.com",
      "useAccountForCharging" : true,
      "allowedMoc" : false,
      "allowedMtc" : false,
      "allowedData" : true,
      "allowedMosms" : false,
      "allowedMtsms" : false,
      "account" : "Test - Second account",
      "reseller" : "Test Reseller"
    } ],
    "hasMore" : false,
    "nbFound" : 11
  }
}
```
### 2.1.4 eSIM activation code
#### Request
```json
{
  "listSubscriber" : {
    "activationCode" : "activation code"
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
  "listSubscriber" : {
    "subscriberList" : [ {
      "imsiList" : [ {
        "id" : 21046,
        "subscriberId" : 21046,
        "imsi" : "248029018000011",
        "startDate" : "2022-03-10T20:29:41",
        "iccid" : "893720401717000011"
      } ],
      "phoneNumberList" : [ {
        "id" : 21040,
        "subscriberId" : 21046,
        "phoneNumber" : "3728803101011",
        "startDate" : "2022-03-10T20:29:41"
      } ],
      "multiImsi" : [ {
        "id" : 21043,
        "subscriberId" : 21046,
        "imsi" : "248029018000011",
        "startDate" : "2022-03-10T20:29:41"
      } ],
      "status" : [ {
        "id" : 21040,
        "subscriberId" : 21046,
        "startDate" : "2022-03-10T20:29:41",
        "status" : "Active"
      } ],
      "sim" : {
        "subscriberId" : 21046,
        "esim" : true,
        "status" : "FREE",
        "pin1" : "0561",
        "pin2" : "1736",
        "puk2" : "50913387",
        "smdpServer" : "smdp.io",
        "activationCode" : "K2-1JL8YT-14S7I6K"
      },
      "subscriberId" : 21046,
      "batchId" : "SPRK_220206_3K_eSIM__20220310192941_435",
      "subscriberName" : "SPRK_eSIM_Eitan_220601_1",
      "accountId" : 37,
      "resellerId" : 10,
      "prepaid" : true,
      "balance" : 0.0,
      "activationDate" : "2022-03-10T20:29:41",
      "lastUsageDate" : "2022-06-01T15:35:34",
      "useAccountForCharging" : true,
      "allowedMoc" : true,
      "allowedMtc" : true,
      "allowedData" : true,
      "allowedMosms" : true,
      "allowedMtsms" : true,
      "account" : "TestSubscribers",
      "reseller" : "Test Reseller 3",
      "lastMcc" : 334,
      "lastMnc" : 50
    } ],
    "hasMore" : false,
    "nbFound" : 1
  }
}
```
#### Remark(s)

- The request here is searching for the exact activation, hence the request will always return 0 or 1 subscriber/sim


## 2.2 affectSubscriberRealPhoneNumber

### Description
This request can be used to affect a real phone number to a subscriber. A real phone number can
be either a MSISDN or a DID.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### 2.2.1 By subscriber ID
#### Request
```json
{
  "affectSubscriberRealPhoneNumber" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "phoneNumber" : 123456789
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
### 2.2.2 By IMSI
#### Request
```json
{
  "affectSubscriberRealPhoneNumber" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "phoneNumber" : 123456789
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.2.3 By ICCID
#### Request
```json
{
  "affectSubscriberRealPhoneNumber" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "phoneNumber" : 123456789
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.2.4 By MSISDN
#### Request
```json
{
  "affectSubscriberRealPhoneNumber" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "phoneNumber" : 123456789
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.2.5 By multi imsi
#### Request
```json
{
  "affectSubscriberRealPhoneNumber" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "phoneNumber" : 123456789
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.2.6 By Activation code
#### Request
```json
{
  "affectSubscriberRealPhoneNumber" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "phoneNumber" : 1123456789
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.3 affectSubscriberFakePhoneNumber

### Description
This request can be used to re-affect a subscriber its fake phone number.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### 2.3.1 By subscriber ID
#### Request
```json
{
  "affectSubscriberFakePhoneNumber" : {
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
  }
}
```
### 2.3.2 By IMSI
#### Request
```json
{
  "affectSubscriberFakePhoneNumber" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.3.3 By ICCID
#### Request
```json
{
  "affectSubscriberFakePhoneNumber" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.3.4 By MSISDN
#### Request
```json
{
  "affectSubscriberFakePhoneNumber" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.3.5 By multi imsi
#### Request
```json
{
  "affectSubscriberFakePhoneNumber" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 2.3.6 By Activation code
#### Request
```json
{
  "affectSubscriberFakePhoneNumber" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


# 3. Prepaid package
## 3.1 listPrepaidPackageTemplate

### Description
This request can be used to list your prepaid package templates. You have several keys to search the templates:
- Reseller: the request will return all the templates of the reseller.
- Location zone: the request wil return all templates linked to that particular location zone.
- Sponsor: The request will list all your templates linked to that particular sponsor.
- Template: By providing a template id you will retrieve this template.

You can also send the request without any search keys. In this case the request will return all your templates.


### 3.1.1 By template Id
#### Request
```json
{
  "listPrepaidPackageTemplate" : {
    "templateId" : 1
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
  "listPrepaidPackageTemplate" : {
    "template" : [ {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 5,
        "locationzonename" : "Test - Benelux"
      },
      "prepaidpackagetemplateid" : 1153,
      "prepaidpackagetemplatename" : "Test - Benelux 17Gb",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 5,
      "databyte" : 18253611008,
      "perioddays" : 1,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 11.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Benelux_17Gb"
    } ]
  }
}
```
### 3.1.2 By reseller
#### Request
```json
{
  "listPrepaidPackageTemplate" : {
    "resellerId" : 1
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
  "listPrepaidPackageTemplate" : {
    "template" : [ {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 5,
        "locationzonename" : "Test - Benelux"
      },
      "prepaidpackagetemplateid" : 1153,
      "prepaidpackagetemplatename" : "Test - Benelux 17Gb",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 5,
      "databyte" : 18253611008,
      "perioddays" : 1,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 11.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Benelux_17Gb"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 2,
        "locationzonename" : "Test - Belgium"
      },
      "prepaidpackagetemplateid" : 1154,
      "prepaidpackagetemplatename" : "Test - Belgium 15GB",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 2,
      "databyte" : 16106127360,
      "perioddays" : 30,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 13.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Belgium_15Gb"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 5,
        "locationzonename" : "Test - Benelux"
      },
      "prepaidpackagetemplateid" : 1155,
      "prepaidpackagetemplatename" : "Test - Benelux 15Gb",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 5,
      "databyte" : 16106127360,
      "perioddays" : 10,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 12.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Benelux_15Gb"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 2,
        "locationzonename" : "Test - Belgium"
      },
      "prepaidpackagetemplateid" : 1156,
      "prepaidpackagetemplatename" : "Test - Belgium 10GB",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 2,
      "databyte" : 16106127360,
      "perioddays" : 30,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 15.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Belgium_15Gb"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 2,
        "locationzonename" : "Test - Belgium"
      },
      "prepaidpackagetemplateid" : 1165,
      "prepaidpackagetemplatename" : "Test - Belgium 10GB NEW",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 2,
      "databyte" : 10737418240,
      "perioddays" : 36,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 11.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Belgium_10Gb"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 21,
        "locationzonename" : "Test - Spain"
      },
      "prepaidpackagetemplateid" : 1204,
      "prepaidpackagetemplatename" : "Test - Spain 10Gb",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 21,
      "databyte" : 10737418240,
      "perioddays" : 30,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 66.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : true,
      "userUiName" : "Spain_10Gb"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 2,
        "locationzonename" : "Test - Belgium"
      },
      "prepaidpackagetemplateid" : 1224,
      "prepaidpackagetemplatename" : "Denis Belgium 20 GB",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 2,
      "databyte" : 21474836480,
      "mocsecond" : 3600,
      "mtcsecond" : 3600,
      "mosmsnumber" : 100,
      "mtsmsnumber" : 200,
      "perioddays" : 30,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 24.0,
      "uiStartAvailablePeriod" : "2022-03-01T17:18:00",
      "uiEndAvailibilityPeriod" : "2022-06-15T17:18:00",
      "uiVisible" : false,
      "userUiName" : "Denis_Belgium_20GB"
    }, {
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "Test-Spons-Display",
        "displayname" : "Test-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 18,
        "locationzonename" : "Test - France"
      },
      "prepaidpackagetemplateid" : 1225,
      "prepaidpackagetemplatename" : "France Test Denis New",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 18,
      "databyte" : 21474836480,
      "mocsecond" : 3600,
      "mtcsecond" : 3600,
      "mosmsnumber" : 100,
      "mtsmsnumber" : 200,
      "perioddays" : 20,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 25.0,
      "uiVisible" : false,
      "userUiName" : "France Test Denis New 20Gb"
    } ]
  }
}
```
### 3.1.3 By sponsor
#### Request
```json
{
  "listPrepaidPackageTemplate" : {
    "sponsorId" : 1
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Check answer in previous request


### 3.1.4 By location zone
#### Request
```json
{
  "listPrepaidPackageTemplate" : {
    "locationZoneId" : 1
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Check answer in previous request


### 3.1.5 No search keys
#### Request
```json
{
  "listPrepaidPackageTemplate" : { }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- If you don't provide any search key, the request will return all the prepaid package templates of all your resellers
- Check answer in previous request


## 3.2 listLocationZoneElement

### Description
This request can be used to list the operators composing a specific location zone.


### Request
```json
{
  "listLocationZoneElement" : 1
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listLocationZoneElement" : {
    "operator" : [ {
      "networkId" : 769,
      "continent" : "Asia",
      "countryCode" : 79,
      "countryName" : "Russian Federation",
      "countryIso2" : "ru",
      "utcOffset" : "+03:00",
      "operatorName" : "OJSC MegaFon",
      "mccMncs" : [ {
        "mcc" : "250",
        "mnc" : "02"
      } ],
      "tadigs" : [ "RUSNW" ]
    } ]
  }
}
```
### Remark(s)

- The numeric value of `listLocationZoneElement` is the id of the location zone


## 3.3 affectPackageToSubscriber

### Description
This request can be used to affect a new prepaid package to a subscriber. The prepaid package
affected to the subscriber will be created based on the package template provided in the request
(you can get the list of template via request `listPrepaidPackageTemplate`).

Please note that this request will activate the subscriber, if it is not active yet. Meaning after
this request (successfully executed), the user can start using its prepaid package, no matter if it
was active or not before the request.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code

The active period of the prepaid package is calculated as following:
- An `activePeriod` with a `start` and `end` date and time is provided in the request: The `start`
  and `end` will be used as start and end date and time for the active period of the package.
  This overrides the validity period configured in the package template.
- A `validityPeriod` expressed as a number of days is provided in the request: The start date
  and time of package is the current date and time. The end date and time of the package is the
  current date and time, plus the number of days mentioned in `validityPeriod`.
- No `activePeriod` nor `validityPeriod`: The start date and time will be the date and time of
  the first successful of the prepaid package template. The end date and time of the package will be
  the first successful usage date and time, plus the number of days for validity configured in the
  package template.


### 3.3.1 By subscriber ID
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "subscriberId" : 1000
    },
    "activePeriod" : {
      "start" : "2023-03-25T11:40:33.490421",
      "end" : "2023-04-24T11:40:33.491451"
    }
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
  "affectPackageToSubscriber" : {
    "iccid" : "893720401615000106",
    "smdpServer" : "smdp.io",
    "activationCode" : "K2-1JL898-DKUTDC",
    "urlQrCode" : "LPA:1$smdp.io$K2-1JL898-DKUTDC",
    "subscriberId" : 18331,
    "esimId" : 37147,
    "subsPackageId" : 414,
    "userSimName" : "Sparks_18331"
  }
}
```
### 3.3.2 By IMSI
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "validityPeriod" : 30
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 3.3.3 By ICCID
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "iccid" : "123456789012345678"
    }
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 3.3.4 By MSISDN
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "msisdn" : "123456789123"
    }
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 3.3.5 By multi imsi
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "multiImsi" : "12345678901234"
    }
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### 3.3.6 By Activation code
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "validityPeriod" : 10
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
#### Remark(s)

- Same content as previous request


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


# 4. Tariff
## 4.1 listResellerTariff

### Description
This request can be used to list the reseller (customer) tariffs (the cost for the customer). You can list them all, or just the
ones of a specific reseller.


### 4.1.1 By reseller
#### Request
```json
{
  "listResellerTariff" : {
    "resellerId" : 1
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
  "listResellerTariff" : {
    "tariff" : [ {
      "resellers" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "roamingplanid" : 1,
      "roamingplanname" : "Test - ResellerAccount",
      "defaultoutgoingvoice" : 0.0,
      "defaultterminatedvoice" : 0.0,
      "defaulttext" : 0.0,
      "defaultdata" : 0.0,
      "resellerid" : 1,
      "defaultmtsms" : 0.0,
      "currencyid" : 1,
      "isusedefaultprices" : false,
      "tariffType" : "RESELLER"
    } ]
  }
}
```
### 4.1.2 No search keys
#### Request
```json
{
  "listResellerTariff" : { }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listResellerTariff" : {
    "tariff" : [ {
      "resellers" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "roamingplanid" : 1,
      "roamingplanname" : "Test - ResellerAccount",
      "defaultoutgoingvoice" : 0.0,
      "defaultterminatedvoice" : 0.0,
      "defaulttext" : 0.0,
      "defaultdata" : 0.0,
      "resellerid" : 1,
      "defaultmtsms" : 0.0,
      "currencyid" : 1,
      "isusedefaultprices" : false,
      "tariffType" : "RESELLER"
    } ]
  }
}
```
#### Remark(s)

- If you don't provide any search key, the request will return all the reseller tariff(s) of all your reseller(s)


## 4.2 listSubscriberTariff

### Description
This request can be used to list the subscriber tariffs. The ones used by a customer to charge
its subscribers. You can list them all, or just the ones of a specific reseller.


### 4.2.1 By reseller
#### Request
```json
{
  "listSubscriberTariff" : {
    "resellerId" : 1
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
  "listSubscriberTariff" : {
    "tariff" : [ {
      "resellers" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "roamingplanid" : 4,
      "roamingplanname" : "Test - Account",
      "defaultoutgoingvoice" : 0.0,
      "defaultterminatedvoice" : 0.0,
      "defaulttext" : 0.0,
      "defaultdata" : 0.0,
      "resellerid" : 1,
      "defaultmtsms" : 0.0,
      "currencyid" : 1,
      "isusedefaultprices" : false,
      "tariffType" : "SUBSCRIBER"
    }, {
      "resellers" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "roamingplanid" : 10,
      "roamingplanname" : "Test - For Subs",
      "defaultoutgoingvoice" : 0.0,
      "defaultterminatedvoice" : 0.0,
      "defaulttext" : 0.0,
      "defaultdata" : 0.0,
      "resellerid" : 1,
      "defaultmtsms" : 0.0,
      "currencyid" : 1,
      "isusedefaultprices" : false,
      "tariffType" : "SUBSCRIBER"
    } ]
  }
}
```
### 4.2.2 No search keys
#### Request
```json
{
  "listSubscriberTariff" : { }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSubscriberTariff" : {
    "tariff" : [ {
      "resellers" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "roamingplanid" : 4,
      "roamingplanname" : "Test - Account",
      "defaultoutgoingvoice" : 0.0,
      "defaultterminatedvoice" : 0.0,
      "defaulttext" : 0.0,
      "defaultdata" : 0.0,
      "resellerid" : 1,
      "defaultmtsms" : 0.0,
      "currencyid" : 1,
      "isusedefaultprices" : false,
      "tariffType" : "SUBSCRIBER"
    }, {
      "resellers" : {
        "resellerid" : 1,
        "resellername" : "Test Reseller"
      },
      "roamingplanid" : 10,
      "roamingplanname" : "Test - For Subs",
      "defaultoutgoingvoice" : 0.0,
      "defaultterminatedvoice" : 0.0,
      "defaulttext" : 0.0,
      "defaultdata" : 0.0,
      "resellerid" : 1,
      "defaultmtsms" : 0.0,
      "currencyid" : 1,
      "isusedefaultprices" : false,
      "tariffType" : "SUBSCRIBER"
    } ]
  }
}
```
#### Remark(s)

- If you don't provide any search key, the request will return all the subscriber tariff(s) of all your reseller(s)


## 4.3 listTariffRule

### Description
This request can be used to list the rules (costs) of a specific tariff.


### Request
```json
{
  "listTariffRule" : 1
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listTariffRule" : {
    "rule" : [ {
      "operator" : {
        "networkId" : 79,
        "continent" : "Europe",
        "countryCode" : 32,
        "countryName" : "Belgium",
        "countryIso2" : "be",
        "utcOffset" : "+01:00",
        "operatorName" : "Proximus PLC",
        "mccMncs" : [ {
          "mcc" : "206",
          "mnc" : "01"
        } ],
        "tadigs" : [ "BELTB" ]
      },
      "currency" : {
        "currencyid" : 1,
        "currencycode" : "EUR",
        "currencyname" : "Euro"
      },
      "roamingplanruleid" : 7198,
      "roamingplanid" : 1,
      "networkid" : 79,
      "sponsoridx" : -1,
      "active" : true,
      "mocallrate" : 2.0,
      "mtcallrate" : 2.0,
      "mosmsrate" : 2.0,
      "mtsmsrate" : 2.0,
      "datarate" : 2.0,
      "currencyid" : 1,
      "startdate" : "2021-11-16T08:16:49",
      "isDiscounted" : true,
      "hidden" : false,
      "dailyCap" : false
    }, {
      "operator" : {
        "networkId" : 477,
        "continent" : "Europe",
        "countryCode" : 39,
        "countryName" : "Italy",
        "countryIso2" : "it",
        "utcOffset" : "+01:00",
        "operatorName" : "H3G S p A ",
        "mccMncs" : [ {
          "mcc" : "222",
          "mnc" : "99"
        } ],
        "tadigs" : [ "ITAH3" ]
      },
      "currency" : {
        "currencyid" : 1,
        "currencycode" : "EUR",
        "currencyname" : "Euro"
      },
      "roamingplanruleid" : 4,
      "roamingplanid" : 1,
      "networkid" : 477,
      "sponsoridx" : -1,
      "active" : true,
      "mocallrate" : 2.0,
      "mtcallrate" : 2.0,
      "mosmsrate" : 2.0,
      "mtsmsrate" : 2.0,
      "datarate" : 2.0,
      "currencyid" : 1,
      "startdate" : "2021-11-16T08:16:49",
      "isDiscounted" : true,
      "hidden" : false,
      "dailyCap" : false
    } ]
  }
}
```
### Remark(s)

- The numeric value of `listTariffRule` is the id of the tariff


# 5. Statistics
## 5.1 getSubscriberActivePeriod

### Description
This request can be used the active period of a subscriber by checking the subscriber usages in DB. The request
will return the date of the first usage and the date of the last usage of the subscriber.


### 5.1.1 By subscriber ID
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "getSubscriberActivePeriod" : {
    "subscriberId" : 3235,
    "period" : {
      "start" : "2022-09-16T08:27:19",
      "end" : "2022-09-19T19:58:43"
    }
  }
}
```
### 5.1.2 By IMSI
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "getSubscriberActivePeriod" : {
    "subscriberId" : 3319
  }
}
```
### 5.1.3 By ICCID
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "getSubscriberActivePeriod" : {
    "subscriberId" : 3235,
    "period" : {
      "start" : "2022-09-16T08:27:19",
      "end" : "2022-09-19T19:58:43"
    }
  }
}
```
### 5.1.4 By MSISDN
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "getSubscriberActivePeriod" : {
    "subscriberId" : 3319
  }
}
```
### 5.1.5 By multi imsi
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "getSubscriberActivePeriod" : {
    "subscriberId" : 3319
  }
}
```
### 5.1.6 By Activation code
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "getSubscriberActivePeriod" : {
    "subscriberId" : 3235,
    "period" : {
      "start" : "2022-09-16T08:27:19",
      "end" : "2022-09-19T19:58:43"
    }
  }
}
```
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.
- This request always returns the subscriber id. So you can use it in any following request with a subscriber as input.
- If the subscriber is found, but there is no usage in DB, in the answer, getSubscriberActivePeriod.period is null


## 5.2 subscriberUsageOverPeriod

### Description
This request can be used to retrieve the daily usage of a subscriber over a certain period. The period
is delimited with a start date (included) and an end date (included). The period cannot exceed 1 week.
If you need statistics about usages over a longer period, you can use the requests using aggregated data.


### 5.2.1 By subscriber ID
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "subscriberUsageOverPeriod" : {
    "total" : {
      "cost" : 110.96954345703125,
      "resellerCost" : 221.9390869140625,
      "subscriberCost" : 0.0,
      "quantityPerType" : {
        "33" : 116360000
      },
      "quantityPerCountry" : [ {
        "mcc" : 206,
        "name" : "Belgium",
        "alpha2" : "be",
        "qty" : 116360000,
        "quantityPerOperator" : [ {
          "mnc" : 1,
          "name" : "Proximus PLC",
          "qty" : 116360000
        } ]
      } ]
    },
    "usages" : [ {
      "subscriberId" : 45043,
      "total" : {
        "cost" : 110.96954345703125,
        "resellerCost" : 221.9390869140625,
        "subscriberCost" : 0.0,
        "quantityPerType" : {
          "33" : 116360000
        },
        "quantityPerCountry" : [ {
          "mcc" : 206,
          "name" : "Belgium",
          "alpha2" : "be",
          "qty" : 116360000,
          "quantityPerOperator" : [ {
            "mnc" : 1,
            "name" : "Proximus PLC",
            "qty" : 116360000
          } ]
        } ]
      },
      "subsPeriodUsages" : [ {
        "day" : "2022-05-27",
        "total" : {
          "cost" : 110.96954345703125,
          "resellerCost" : 221.9390869140625,
          "subscriberCost" : 0.0,
          "quantityPerType" : {
            "33" : 116360000
          },
          "quantityPerCountry" : [ {
            "mcc" : 206,
            "name" : "Belgium",
            "alpha2" : "be",
            "qty" : 116360000,
            "quantityPerOperator" : [ {
              "mnc" : 1,
              "name" : "Proximus PLC",
              "qty" : 116360000
            } ]
          } ]
        },
        "subsDailyUsages" : [ {
          "subscriberId" : 45043,
          "sessionId" : "0003-diamproxy.roamability.gy-sctp-spgw-wro01.lte.orange.pl;1674744814;222111258;5f4b7491-31a02",
          "usageDateUtc" : "2022-05-27T14:14:12",
          "usageType" : 33,
          "accountId" : 1,
          "accountName" : "Unknown - 1",
          "resellerId" : 1,
          "resellerName" : "PDEL Reseller",
          "mcc" : 206,
          "country" : "Belgium",
          "countryAlpha2" : "be",
          "operator" : "Proximus PLC",
          "mnc" : 1,
          "quantity" : 10000000,
          "cost" : 9.5367431640625,
          "costPlanId" : 7,
          "costPlanRuleId" : 7204,
          "resellerCost" : 19.073486328125,
          "resellerPlanId" : 1,
          "resellerPlanRuleId" : 7198,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPrepaidPackageId" : 10,
          "subscriberPrepaidPackageQty" : 10000000,
          "lac" : 3216,
          "cellId" : 4866,
          "rat" : "2G - GERAN",
          "imei" : "351934048890953",
          "upBitrate" : 472000,
          "downBitrate" : 472000,
          "qci" : 8,
          "apn" : "data.rewicom.net",
          "imsiPrefix" : 99999,
          "sponsorImsi" : 999990000002000,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 45043,
          "sessionId" : "0003-diamproxy.roamability.gy-sctp-spgw-wro01.lte.orange.pl;1674744814;222111258;5f4b7491-31a02",
          "usageDateUtc" : "2022-05-27T14:10:03",
          "usageType" : 33,
          "accountId" : 1,
          "accountName" : "Unknown - 1",
          "resellerId" : 1,
          "resellerName" : "PDEL Reseller",
          "mcc" : 206,
          "country" : "Belgium",
          "countryAlpha2" : "be",
          "operator" : "Proximus PLC",
          "mnc" : 1,
          "quantity" : 10000000,
          "cost" : 9.5367431640625,
          "costPlanId" : 7,
          "costPlanRuleId" : 7204,
          "resellerCost" : 19.073486328125,
          "resellerPlanId" : 1,
          "resellerPlanRuleId" : 7198,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPrepaidPackageId" : 4,
          "subscriberPrepaidPackageQty" : 10000000,
          "lac" : 3216,
          "cellId" : 4866,
          "rat" : "2G - GERAN",
          "imei" : "351934048890953",
          "upBitrate" : 472000,
          "downBitrate" : 472000,
          "qci" : 8,
          "apn" : "data.rewicom.net",
          "imsiPrefix" : 99999,
          "sponsorImsi" : 999990000002000,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 45043,
          "sessionId" : "0003-diamproxy.roamability.gy-sctp-spgw-wro01.lte.orange.pl;1674744814;222111258;5f4b7491-31a02",
          "usageDateUtc" : "2022-05-27T13:45:51",
          "usageType" : 33,
          "accountId" : 1,
          "accountName" : "Unknown - 1",
          "resellerId" : 1,
          "resellerName" : "PDEL Reseller",
          "mcc" : 206,
          "country" : "Belgium",
          "countryAlpha2" : "be",
          "operator" : "Proximus PLC",
          "mnc" : 1,
          "quantity" : 10000000,
          "cost" : 9.5367431640625,
          "costPlanId" : 7,
          "costPlanRuleId" : 7204,
          "resellerCost" : 19.073486328125,
          "resellerPlanId" : 1,
          "resellerPlanRuleId" : 7198,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPrepaidPackageId" : 4,
          "subscriberPrepaidPackageQty" : 10000000,
          "lac" : 3216,
          "cellId" : 4866,
          "rat" : "2G - GERAN",
          "imei" : "351934048890953",
          "upBitrate" : 472000,
          "downBitrate" : 472000,
          "qci" : 8,
          "apn" : "data.rewicom.net",
          "imsiPrefix" : 99999,
          "sponsorImsi" : 999990000002000,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 45043,
          "sessionId" : "0003-diamproxy.roamability.gy-sctp-spgw-wro01.lte.orange.pl;1674744814;222111258;5f4b7491-31a02",
          "usageDateUtc" : "2022-05-27T13:41:12",
          "usageType" : 33,
          "accountId" : 1,
          "accountName" : "Unknown - 1",
          "resellerId" : 1,
          "resellerName" : "PDEL Reseller",
          "mcc" : 206,
          "country" : "Belgium",
          "countryAlpha2" : "be",
          "operator" : "Proximus PLC",
          "mnc" : 1,
          "quantity" : 38180000,
          "cost" : 36.411285400390625,
          "costPlanId" : 7,
          "costPlanRuleId" : 7204,
          "resellerCost" : 72.82257080078125,
          "resellerPlanId" : 1,
          "resellerPlanRuleId" : 7198,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPrepaidPackageId" : 4,
          "subscriberPrepaidPackageQty" : 38180000,
          "lac" : 219,
          "cellId" : 61478,
          "rat" : "2G - GERAN",
          "imei" : "868017031911303",
          "upBitrate" : 64000,
          "downBitrate" : 240000,
          "qci" : 8,
          "apn" : "uinternet",
          "imsiPrefix" : 99999,
          "sponsorImsi" : 999990000002000,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 45043,
          "sessionId" : "0003-diamproxy.roamability.gy-sctp-spgw-wro01.lte.orange.pl;1674744814;222111258;5f4b7491-31a02",
          "usageDateUtc" : "2022-05-27T13:25:03",
          "usageType" : 33,
          "accountId" : 1,
          "accountName" : "Unknown - 1",
          "resellerId" : 1,
          "resellerName" : "PDEL Reseller",
          "mcc" : 206,
          "country" : "Belgium",
          "countryAlpha2" : "be",
          "operator" : "Proximus PLC",
          "mnc" : 1,
          "quantity" : 10000000,
          "cost" : 9.5367431640625,
          "costPlanId" : 7,
          "costPlanRuleId" : 7204,
          "resellerCost" : 19.073486328125,
          "resellerPlanId" : 1,
          "resellerPlanRuleId" : 7198,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPrepaidPackageId" : 4,
          "subscriberPrepaidPackageQty" : 10000000,
          "lac" : 3216,
          "cellId" : 4866,
          "rat" : "2G - GERAN",
          "imei" : "351934048890953",
          "upBitrate" : 472000,
          "downBitrate" : 472000,
          "qci" : 8,
          "apn" : "data.rewicom.net",
          "imsiPrefix" : 99999,
          "sponsorImsi" : 999990000002000,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 45043,
          "sessionId" : "0003-diamproxy.roamability.gy-sctp-spgw-wro01.lte.orange.pl;1674744814;222111258;5f4b7491-31a02",
          "usageDateUtc" : "2022-05-27T13:23:23",
          "usageType" : 33,
          "accountId" : 1,
          "accountName" : "Unknown - 1",
          "resellerId" : 1,
          "resellerName" : "PDEL Reseller",
          "mcc" : 206,
          "country" : "Belgium",
          "countryAlpha2" : "be",
          "operator" : "Proximus PLC",
          "mnc" : 1,
          "quantity" : 38180000,
          "cost" : 36.411285400390625,
          "costPlanId" : 7,
          "costPlanRuleId" : 7204,
          "resellerCost" : 72.82257080078125,
          "resellerPlanId" : 1,
          "resellerPlanRuleId" : 7198,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPrepaidPackageId" : 4,
          "subscriberPrepaidPackageQty" : 38180000,
          "lac" : 219,
          "cellId" : 61478,
          "rat" : "2G - GERAN",
          "imei" : "868017031911303",
          "upBitrate" : 64000,
          "downBitrate" : 240000,
          "qci" : 8,
          "apn" : "uinternet",
          "imsiPrefix" : 99999,
          "sponsorImsi" : 999990000002000,
          "accountChargeEntity" : false
        } ]
      } ]
    } ]
  }
}
```
### 5.2.2 By IMSI
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.2.3 By ICCID
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.2.4 By MSISDN
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.2.5 By multi imsi
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.2.6 By Activation code
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 5.3 subscriberNetworkEventsOverPeriod

### Description
This request can be used to retrieve the network events of a subscriber over a certain period. The period
is delimited with a start date (included) and an end date (included). The period cannot exceed 1 week.


### 5.3.1 By subscriber ID
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  "subscriberNetworkEventsOverPeriod" : {
    "mapAnswer" : {
      "events" : [ {
        "eventTime" : "2022-11-21T23:08:51.333+01:00",
        "mcc" : 0,
        "mnc" : 0,
        "countryName" : "N/A",
        "countryAlpha2" : "N/A",
        "operator" : "N/A",
        "service" : "dmi",
        "o_gt" : "972521100089",
        "o_ssn" : "149",
        "d_gt" : "37250980917",
        "d_ssn" : "6",
        "opcode" : "67",
        "shortCode" : "P-MS",
        "longCode" : "purgeMS",
        "result" : "N/A",
        "in_imsi" : "248010415100003",
        "protocol" : "MAP",
        "acn" : "04000001001b03",
        "host" : "stp1"
      } ]
    },
    "s6aAnswer" : {
      "events" : [ {
        "eventTime" : "2022-11-21T16:03:47.842+01:00",
        "service" : "dmi_diam",
        "cmdCode" : "321",
        "cmdNameShort" : "PUR",
        "cmdNameLong" : "Purge-UE-Request",
        "protocol" : "S6a",
        "sponsor_imsi" : "248010415100003",
        "subs_imsi" : "248010415100003",
        "mvno" : "Sparks",
        "code" : "PUR_NOR",
        "oper_allowed" : "N/A",
        "customer" : "Sparks",
        "session" : "bcmmor1.epc.mnc002.mcc425.3gppnetwork.org;0316107b;bd6d4e5b;5cab64ce",
        "orig_realm" : "epc.mnc002.mcc425.3gppnetwork.org",
        "orig_host" : "bcmmor1.epc.mnc002.mcc425.3gppnetwork.org",
        "dest_realm" : "epc.mnc001.mcc248.3gppnetwork.org",
        "host" : "stp2",
        "user_apn" : "N/A",
        "sponsor" : "SP01_RESTR",
        "countryName" : "N/A",
        "countryAlpha2" : "N/A",
        "operator" : "N/A"
      } ]
    },
    "gyAnswer" : {
      "events" : [ {
        "eventTime" : "2022-11-20T14:09:18.795+01:00",
        "hopByHopS" : "607cb75f",
        "endToEndS" : "e4fe080a",
        "hopByHopL" : 1618786143,
        "endToEndL" : 3841853450,
        "originHost" : "travelsim-datak6.emt.ee",
        "originRealm" : "emt.ee",
        "requestType" : "Term",
        "session" : "ee-cmg02cgy.pgw.epc.mnc001.mcc248.3gppnetwork.org;39607f64;637a268c;248010415100003-130303d5",
        "msisdn" : "3728802100003",
        "imei" : "353041112627481",
        "apn" : "internet.emt.ee",
        "ratTypes" : "3G - UTRAN",
        "userLocationInfoMCC" : "425",
        "userLocationInfoMNC" : "02",
        "userLocationInfoLAC" : "42731",
        "usedUnits" : "1792819",
        "responseCode" : "2001",
        "sgsnip" : "62.90.68.114",
        "rreResponse" : "OK",
        "ratingGroup" : "6",
        "rreAllowedQuota" : "N/A",
        "countryName" : "Israel",
        "countryAlpha2" : "il",
        "operator" : "Cellcom Israel Ltd ",
        "userLocationInfoSAC" : "49814"
      } ]
    }
  }
}
```
### 5.3.2 By IMSI
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.3.3 By ICCID
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.3.4 By MSISDN
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.3.5 By multi imsi
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### 5.3.6 By Activation code
#### Request
```json
{
  "getSubscriberActivePeriod" : {
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
  }
}
```
#### Remark(s)

- Same content as previous request


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


# 6. SMS
## 6.1 sendMtSms

### Description
This request can be used to send a SMS to a subscriber belonging to a visible reseller. The SMS
will be sent via MAP MT-Forward-Sm request.

This SMS to send can contain unicode characters. Unicode characters must be provided as /uXXXX,where XXXX is a hex value.
In order to send just a `/u`, simply send it as `//u`.

If there is at least one Unicode character in the text, then whole text will be converted into Unicode.

Example:<br>
Original message: `Test 123 Тест`<br>
Message in JSON: `Test 123 /u0422/u0435/u0441/u0442`


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|imsi|Mandatory|IMSI of the destination that will receive the SMS|
|text|Mandatory|The text to send, with support of Unicode.|
|senderId|Mandatory|MSISDN or any text identification of the sender|


### Request
```json
{
  "sendMtSms" : {
    "imsi" : 123456789,
    "text" : "Msg to send",
    "senderId" : "Sender"
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  }
}
```
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

