## [1 Reseller](#11-listreselleraccount)

[1.1 listResellerAccount](#11-listreselleraccount)

[1.2 modifyAccountBalance](#12-modifyaccountbalance)

## [2 Subscriber](#21-listsubscriber)

[2.1 listSubscriber](#21-listsubscriber)

[2.2 affectSubscriberRealPhoneNumber](#22-affectsubscriberrealphonenumber)

[2.3 affectSubscriberFakePhoneNumber](#23-affectsubscriberfakephonenumber)

[2.4 getSimProviderStatus](#24-getsimproviderstatus)

[2.5 modifySubscriberBalance](#25-modifysubscriberbalance)

[2.6 modifySubscriberPrepaidPackageLimits](#26-modifysubscriberprepaidpackagelimits)

[2.7 modifySubscriberPrepaidPackageExpDate](#27-modifysubscriberprepaidpackageexpdate)

[2.8 modifySubscriberPrepaidPackageStatus](#28-modifysubscriberprepaidpackagestatus)

## [3 Prepaid package](#31-listprepaidpackagetemplate)

[3.1 listPrepaidPackageTemplate](#31-listprepaidpackagetemplate)

[3.2 listLocationZoneElement](#32-listlocationzoneelement)

[3.3 affectPackageToSubscriber](#33-affectpackagetosubscriber)

[3.4 listSubscriberPrepaidPackages](#34-listsubscriberprepaidpackages)

[3.5 listDestinationListPrefix](#35-listdestinationlistprefix)

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
        "balance" : 660.5500000000001,
        "packageOnly" : false
      }, {
        "id" : 7,
        "name" : "Test - Subs X",
        "balance" : 1000.0,
        "packageOnly" : false
      }, {
        "id" : 55,
        "name" : "FUT",
        "balance" : 70.06,
        "packageOnly" : false
      }, {
        "id" : 104,
        "name" : "test from UI",
        "balance" : 100.0,
        "packageOnly" : false
      }, {
        "id" : 125,
        "name" : "Denis new account",
        "balance" : 0.0,
        "packageOnly" : false
      } ]
    }, {
      "id" : 10,
      "name" : "Test Reseller 3",
      "account" : [ {
        "id" : 37,
        "name" : "TestSubscribers",
        "balance" : 97.80718309495325,
        "packageOnly" : false
      } ]
    }, {
      "id" : 58,
      "name" : "Reseller XYZ",
      "account" : [ {
        "id" : 118,
        "name" : "Test dev account name",
        "balance" : 100.0,
        "packageOnly" : false
      }, {
        "id" : 119,
        "name" : "Test dev account name 2",
        "balance" : 100.0,
        "packageOnly" : false
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
        "balance" : 97.80718309495325,
        "packageOnly" : false
      } ]
    } ]
  }
}
```
## 1.2 modifyAccountBalance

### Description
This request can be used to adapt the balance of an account. The balance can either:
- Be adapted: You can add or remove a certain amount from the balance. The amount you need to provide in the request will be added to the current balance.  You can provide a negative amount and the balance will be decreased. Please note that balance  cannot become negative, in such a case the balance will be set to 0.
- Set to a new value: In this case you provide the new amount you want to set the balance to.

This request is logged in the system DB and you can see them in the UI, in the `Account` -> `Transaction` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|accountId|Mandatory|The ID of the account to modify|
|amount|Mandatory|The amount to add to the current balance|
|setBalance|Optional|true => balance will be set to provided amount, false => balance will be adapted|
|description|Optional|A description giving information about the reason of this balance adjustment|


### 1.2.1 Update balance
#### Request
```json
{
  "modifyAccountBalance" : {
    "accountId" : 132,
    "amount" : -123.25,
    "description" : "Optional description"
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
### 1.2.2 Set balance
#### Request
```json
{
  "modifyAccountBalance" : {
    "accountId" : 132,
    "amount" : 123.25,
    "description" : "Optional description",
    "setBalance" : true
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
        "id" : 36904,
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
        "id" : 36905,
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
        "id" : 36904,
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
        "id" : 36905,
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
        "id" : 36904,
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
        "id" : 36905,
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
        "id" : 36904,
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


## 2.4 getSimProviderStatus

### Description
This request can be used to retrieve the status of the eSIM from the eSIM provider system. It returns in fact the
status history of the eSIM. The current status is the one with no `end` date.

Note that the statuses are sorted by `start` date in descending order (most recent date first).


### Request
```json
{
  "getSimProviderStatus" : 1234
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "getSimProviderStatus" : [ {
    "simId" : 36862,
    "status" : "Enable",
    "start" : "2023-04-06T09:55:08",
    "profileType" : "SPRK_230218_NoApplet_SP02",
    "statusModification" : "Executed-Success"
  }, {
    "simId" : 36862,
    "status" : "Enable",
    "start" : "2023-04-01T09:55:08",
    "end" : "2023-04-06T09:55:08",
    "profileType" : "SPRK_230218_NoApplet_SP02",
    "statusModification" : "Executed-Success"
  } ]
}
```
### Remark(s)

- The numeric value of `getSimProviderStatus` is the id of the eSIM. You can find it in the answer of `listSubscriber`: subscriberList -> sim -> id


## 2.5 modifySubscriberBalance

### Description
This request can be used to adapt the balance of a subscriber. The balance can either:
- Be adapted: You can add or remove a certain amount from the balance. The amount you need to provide in the request will be added to the current balance.  You can provide a negative amount and the balance will be decreased. Please note that balance  cannot become negative, in such a case the balance will be set to 0.
- Set to a new value: In this case you provide the new amount you want to set the balance to.

This request is logged in the system DB and you can see them in the UI, in the `Subscriber` -> `Transaction` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|subscriber|Mandatory|One of the subscriber identifier see `Subscriber identifiers` in [OcsObjects.md](OcsObjects.md)|
|amount|Mandatory|The amount to add to the current balance|
|setBalance|Optional|true => balance will be set to provided amount, false => balance will be adapted|
|description|Optional|A description giving information about the reason of this balance adjustment|


### 2.5.1 Update balance
#### Request
```json
{
  "modifySubscriberBalance" : {
    "subscriber" : {
      "subscriberId" : 123
    },
    "amount" : -123.25,
    "description" : "Optional description"
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
### 2.5.2 Set balance
#### Request
```json
{
  "modifySubscriberBalance" : {
    "subscriber" : {
      "subscriberId" : 123
    },
    "amount" : -123.25,
    "description" : "Optional description",
    "setBalance" : true
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
## 2.6 modifySubscriberPrepaidPackageLimits

### Description
This request can be used to adapt one or more limits (max volume, max SMS, minutes of call) of a
subscriber prepaid package.

This request is logged in the system DB and you can see them in the UI, in the `Subscriber prepaid package` -> `History` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|packageId|Mandatory|The ID of the subscriber prepaid package to adapt|
|newLimits.dataByte|Mandatory|The new limit for the data volume of this package, in bytes. Set to `null` to leave unchanged.|
|newLimits.mocSecond|Mandatory|The new limit for the MO calls of this package, in minutes. Set to `null` to leave unchanged.|
|newLimits.mtcSecond|Mandatory|The new limit for the MT calls of this package, in minutes. Set to `null` to leave unchanged.|
|newLimits.moSms|Mandatory|The new limit for the MO SMS of this package, in number of SMS. Set to `null` to leave unchanged.|
|newLimits.mtSms|Mandatory|The new limit for the MT SMS of this package, number of SMS. Set to `null` to leave unchanged.|
|comment|Optional|A description giving information about the reason of this adjustment|


### Request
```json
{
  "modifySubscriberPrepaidPackageLimits" : {
    "packageId" : 123,
    "newLimits" : {
      "dataByte" : 1073741824,
      "mocSecond" : 60,
      "mtcSecond" : 90,
      "moSms" : 100,
      "mtSms" : 200
    },
    "comment" : "Optional comment"
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
## 2.7 modifySubscriberPrepaidPackageExpDate

### Description
This request can be used to adapt the expiration date of a subscriber prepaid package.

This request is logged in the system DB and you can see them in the UI, in the `Subscriber prepaid package` -> `History` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|packageId|Mandatory|The ID of the subscriber prepaid package to adapt.|
|newPeriod|Mandatory|The number of days between the start validity date and the new expiration date. You don't really need to update this value, but if you want to keep data consistent, provide the correct value.|
|newDateUtc|Optional|The new expiration date for the subscriber prepaid package.|


### Request
```json
{
  "modifySubscriberPrepaidPackageExpDate" : {
    "packageId" : 123,
    "newPeriod" : 45,
    "newDateUtc" : "2023-09-08T11:28:55.184244"
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
## 2.8 modifySubscriberPrepaidPackageStatus

### Description
This request can be used to adapt the status of a subscriber prepaid package. You can activate or deactivate the package.
A deactivated package can no longer be used by the subscriber.

This request is logged in the system DB and you can see them in the UI, in the `Subscriber prepaid package` -> `History` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|subsPrepaidPackageId|Mandatory|The ID of the subscriber prepaid package to adapt.|
|active|Mandatory|`true` => prepaid package is active, `false` => prepaid package is blocked.|


### Request
```json
{
  "modifySubscriberPrepaidPackageStatus" : {
    "subsPrepaidPackageId" : 123,
    "active" : false
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
        "sponsorname" : "PDEL-Spons-Display",
        "displayname" : "PDEL-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "PDEL Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 21,
        "locationzonename" : "PDEL - Spain"
      },
      "prepaidpackagetemplateid" : 1204,
      "prepaidpackagetemplatename" : "PDEL - Spain 10Gb",
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
      "uiVisible" : false,
      "userUiName" : "Spain_10Gb"
    }, {
      "rdbDestinationZones" : {
        "destinationzoneid" : 1,
        "destinationzonename" : "PDEL Test - 7"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "PDEL Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 2,
        "locationzonename" : "PDEL - Belgium"
      },
      "prepaidpackagetemplateid" : 1207,
      "prepaidpackagetemplatename" : "blalbla",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 2,
      "destinationzoneid" : 1,
      "databyte" : 10737418240,
      "perioddays" : 30,
      "deleted" : false,
      "cost" : 50.0,
      "uiStartAvailablePeriod" : "2022-09-24T11:30:00",
      "uiEndAvailibilityPeriod" : "2022-09-30T11:30:00",
      "uiVisible" : false,
      "userUiName" : "blalbla"
    }, {
      "rdbDestinationZones" : {
        "destinationzoneid" : 1,
        "destinationzonename" : "PDEL Test - 7"
      },
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "PDEL-Spons-Display",
        "displayname" : "PDEL-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "PDEL Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 2,
        "locationzonename" : "PDEL - Belgium"
      },
      "prepaidpackagetemplateid" : 1224,
      "prepaidpackagetemplatename" : "Denis Belgium 20 GB",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 2,
      "destinationzoneid" : 1,
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
      "rdbDestinationZones" : {
        "destinationzoneid" : 5,
        "destinationzonename" : "Denis Destination list"
      },
      "sponsors" : {
        "sponsorid" : 104,
        "sponsorname" : "SP04",
        "displayname" : "SP04"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "PDEL Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "prepaidpackagetemplateid" : 2214,
      "prepaidpackagetemplatename" : "Denis Italy",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 27,
      "destinationzoneid" : 5,
      "databyte" : 1073741824,
      "perioddays" : 10,
      "deleted" : false,
      "esimSponsor" : 104,
      "cost" : 9.99,
      "uiStartAvailablePeriod" : "2022-06-20T16:47:41",
      "uiVisible" : false
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
      "rdbDestinationZones" : {
        "destinationzoneid" : 1,
        "destinationzonename" : "PDEL Test - 7"
      },
      "sponsors" : {
        "sponsorid" : 1,
        "sponsorname" : "PDEL-Spons-Display",
        "displayname" : "PDEL-Spons-Display"
      },
      "reseller" : {
        "resellerid" : 1,
        "resellername" : "PDEL Reseller"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 18,
        "locationzonename" : "PDEL - France"
      },
      "prepaidpackagetemplateid" : 1225,
      "prepaidpackagetemplatename" : "France PDEL Denis New",
      "resellerid" : 1,
      "priority" : 1,
      "locationzoneid" : 18,
      "destinationzoneid" : 1,
      "databyte" : 21474836480,
      "mocsecond" : 3600,
      "mtcsecond" : 3600,
      "mosmsnumber" : 100,
      "mtsmsnumber" : 200,
      "perioddays" : 20,
      "deleted" : false,
      "esimSponsor" : 1,
      "cost" : 25.0,
      "uiStartAvailablePeriod" : "2022-06-20T16:47:41",
      "uiVisible" : false,
      "userUiName" : "France PDEL Denis New 20Gb"
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


### 3.1.5 By destination list
#### Request
```json
{
  "listPrepaidPackageTemplate" : {
    "destinationListId" : 1207
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


### 3.1.6 No search keys
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
      "start" : "2023-09-08T11:28:55.227288",
      "end" : "2023-10-08T11:28:55.227302"
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


## 3.4 listSubscriberPrepaidPackages

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
|listSubscriberPrepaidPackages.packages|Mandatory|Array of subscriber prepaid packages, see `Subscriber prepaid package` in [OcsObjects.md](OcsObjects.md). If the subscriber doesn't have any prepaid package, this array will be empty.|


### 3.4.1 By subscriber ID
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
        "destinationzoneid" : 1,
        "destinationzonename" : "PDEL Test - 7"
      },
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 30,
        "prepaidpackagetemplatename" : "PDEL - Italy 20Gb"
      },
      "subscriberprepaidpackageid" : 83,
      "subscriberid" : 4,
      "priority" : 1,
      "locationzoneid" : 27,
      "destinationzoneid" : 1,
      "pckdatabyte" : 21474836480,
      "pckmocsecond" : 100,
      "pckmtcsecond" : 100,
      "pckmosmsnumber" : 500,
      "pckmtsmsnumber" : 500,
      "tsassigned" : "2022-10-13T15:04:43",
      "tsactivationutc" : "2023-02-22T09:52:53",
      "tsexpirationutc" : "2023-09-30T12:09:04",
      "useddatabyte" : 30971520,
      "usedmocsecond" : 100,
      "usedmocvoipsecond" : 75,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 30,
      "cost" : 23.0,
      "templateId" : 30,
      "esimId" : 64612,
      "active" : true
    }, {
      "rdbLocationZones" : {
        "locationzoneid" : 27,
        "locationzonename" : "PDEL - Italy"
      },
      "packageTemplate" : {
        "prepaidpackagetemplateid" : 30,
        "prepaidpackagetemplatename" : "PDEL - Italy 20Gb"
      },
      "subscriberprepaidpackageid" : 989,
      "subscriberid" : 4,
      "priority" : 2,
      "locationzoneid" : 27,
      "pckdatabyte" : 21474836480,
      "pckmocsecond" : 0,
      "pckmtcsecond" : 0,
      "pckmosmsnumber" : 0,
      "pckmtsmsnumber" : 0,
      "tsassigned" : "2022-10-13T15:04:43",
      "tsactivationutc" : "2023-02-22T09:52:53",
      "tsexpirationutc" : "2023-07-27T08:02:54",
      "useddatabyte" : 10971520,
      "usedmocsecond" : 0,
      "usedmocvoipsecond" : 0,
      "usedmtcsecond" : 0,
      "usedmosmsnumber" : 0,
      "usedmtsmsnumber" : 0,
      "perioddays" : 30,
      "cost" : 23.0,
      "templateId" : 30,
      "esimId" : 64612,
      "active" : false
    }, {
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
      "pckdatabyte" : 1073741824,
      "pckmocsecond" : 0,
      "pckmtcsecond" : 0,
      "pckmosmsnumber" : 0,
      "pckmtsmsnumber" : 0,
      "tsassigned" : "2023-08-01T13:25:08",
      "useddatabyte" : 0,
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
    } ],
    "callUseSingleCounter" : false
  }
}
```
### 3.4.2 By IMSI
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


### 3.4.3 By ICCID
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


### 3.4.4 By MSISDN
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


### 3.4.5 By multi imsi
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


### 3.4.6 By Activation code
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


## 3.5 listDestinationListPrefix

### Description
This request can be used to list the prefix(es) of a specific destination list.


### Request
```json
{
  "listDestinationListPrefix" : 1
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listDestinationListPrefix" : {
    "prefixes" : [ "12", "32", "7" ],
    "resellerId" : 1,
    "listId" : 1,
    "listName" : "Test - 7"
  }
}
```
### Remark(s)

- The numeric value of `listDestinationListPrefix` is the id of the destination list


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

Usage type:

| Numeric value | Usage type |
| --- | --- |
| 1 | MOC |
| 15 | MTC |
| 21 | MO-SMS |
| 22 | MT-SMS |
| 33 | Data |
| 40 | MOC VoIP |
| 41 | MTC VoIP |


### 5.2.1 By subscriber ID
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "period" : {
      "start" : "2023-09-08",
      "end" : "2023-09-03"
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
  "subscriberUsageOverPeriod" : {
    "total" : {
      "resellerCost" : 0.6963018882751465,
      "subscriberCost" : 0.6963018882751465,
      "quantityPerType" : {
        "1" : 64,
        "33" : 10485840,
        "40" : 9
      },
      "quantityPerCountry" : [ {
        "mcc" : 250,
        "name" : "Russian Federation",
        "alpha2" : "ru",
        "qty" : 10485913,
        "quantityPerOperator" : [ {
          "mnc" : 1,
          "name" : "PJSC Mobile TeleSystems MTS",
          "qty" : 10485913
        } ]
      } ]
    },
    "usages" : [ {
      "subscriberId" : 18037,
      "total" : {
        "resellerCost" : 0.6963018882751465,
        "subscriberCost" : 0.6963018882751465,
        "quantityPerType" : {
          "1" : 64,
          "33" : 10485840,
          "40" : 9
        },
        "quantityPerCountry" : [ {
          "mcc" : 250,
          "name" : "Russian Federation",
          "alpha2" : "ru",
          "qty" : 10485913,
          "quantityPerOperator" : [ {
            "mnc" : 1,
            "name" : "PJSC Mobile TeleSystems MTS",
            "qty" : 10485913
          } ]
        } ]
      },
      "subsPeriodUsages" : [ {
        "day" : "2022-06-16",
        "total" : {
          "resellerCost" : 0.6963018882751465,
          "subscriberCost" : 0.6963018882751465,
          "quantityPerType" : {
            "1" : 64,
            "33" : 10485840,
            "40" : 9
          },
          "quantityPerCountry" : [ {
            "mcc" : 250,
            "name" : "Russian Federation",
            "alpha2" : "ru",
            "qty" : 10485913,
            "quantityPerOperator" : [ {
              "mnc" : 1,
              "name" : "PJSC Mobile TeleSystems MTS",
              "qty" : 10485913
            } ]
          } ]
        },
        "subsDailyUsages" : [ {
          "subscriberId" : 18037,
          "sessionId" : "ee-cmg02cgy.pgw.epc.mnc001.mcc248.3gppnetwork.org;2347c4a1;62ab0e46;248010416000008-12c41685",
          "usageDateUtc" : "2022-06-16T11:17:08",
          "usageType" : 33,
          "accountId" : 22,
          "accountName" : "Unknown - 22",
          "resellerId" : 7,
          "resellerName" : "Sparks Test",
          "mcc" : 250,
          "country" : "Russian Federation",
          "countryAlpha2" : "ru",
          "operator" : "PJSC Mobile TeleSystems MTS",
          "mnc" : 1,
          "quantity" : 10485760,
          "resellerCost" : 0.2475,
          "resellerPlanId" : 400,
          "resellerPlanRuleId" : 1564,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.2475,
          "subscriberPlanId" : 400,
          "subscriberPlanRuleId" : 1564,
          "subscriberCurrencyId" : 1,
          "subscriberConvertRate" : 1.0,
          "subscriberPrepaidPackageQty" : 0,
          "lac" : 12361,
          "cellId" : 116115764,
          "rat" : "4G - LTE",
          "imei" : "354647888013844",
          "upBitrate" : 0,
          "downBitrate" : 0,
          "qci" : 0,
          "apn" : "internet.emt.ee",
          "imsiPrefix" : 24801,
          "sponsorImsi" : 248010416000008,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 18037,
          "sessionId" : "37945396-1655377585",
          "usageDateUtc" : "2022-06-16T11:06:51",
          "usageType" : 40,
          "accountId" : 22,
          "accountName" : "Unknown - 22",
          "resellerId" : 7,
          "resellerName" : "Sparks Test",
          "mcc" : 250,
          "country" : "Russian Federation",
          "countryAlpha2" : "ru",
          "operator" : "PJSC Mobile TeleSystems MTS",
          "mnc" : 1,
          "quantity" : 4,
          "resellerCost" : 0.0,
          "resellerPlanId" : 4,
          "resellerPlanRuleId" : 19,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPlanId" : 4,
          "subscriberPlanRuleId" : 19,
          "subscriberCurrencyId" : 1,
          "subscriberConvertRate" : 1.0,
          "subscriberPrepaidPackageQty" : 0,
          "otherPartyNumber" : "79811564198",
          "imsiPrefix" : 24801,
          "sponsorImsi" : 248010416000008,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 18037,
          "sessionId" : "37945396-1655377585",
          "usageDateUtc" : "2022-06-16T11:06:51",
          "usageType" : 1,
          "accountId" : 22,
          "accountName" : "Unknown - 22",
          "resellerId" : 7,
          "resellerName" : "Sparks Test",
          "mcc" : 250,
          "country" : "Russian Federation",
          "countryAlpha2" : "ru",
          "operator" : "PJSC Mobile TeleSystems MTS",
          "mnc" : 1,
          "quantity" : 4,
          "resellerCost" : 0.028050000000000002,
          "resellerPlanId" : 400,
          "resellerPlanRuleId" : 1564,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.028050000000000002,
          "subscriberPlanId" : 400,
          "subscriberPlanRuleId" : 1564,
          "subscriberCurrencyId" : 1,
          "subscriberConvertRate" : 1.0,
          "subscriberPrepaidPackageQty" : 0,
          "otherPartyNumber" : "3726503919",
          "imsiPrefix" : 24801,
          "sponsorImsi" : 248010416000008,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 18037,
          "sessionId" : "ee-cmg01cgy.pgw.epc.mnc001.mcc248.3gppnetwork.org;08d2465b;62ab0c78;248010416000008-3f6e0a45",
          "usageDateUtc" : "2022-06-16T11:04:36",
          "usageType" : 33,
          "accountId" : 22,
          "accountName" : "Unknown - 22",
          "resellerId" : 7,
          "resellerName" : "Sparks Test",
          "mcc" : 250,
          "country" : "Russian Federation",
          "countryAlpha2" : "ru",
          "operator" : "PJSC Mobile TeleSystems MTS",
          "mnc" : 1,
          "quantity" : 80,
          "resellerCost" : 1.888275146484375E-6,
          "resellerPlanId" : 400,
          "resellerPlanRuleId" : 1564,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 1.888275146484375E-6,
          "subscriberPlanId" : 400,
          "subscriberPlanRuleId" : 1564,
          "subscriberCurrencyId" : 1,
          "subscriberConvertRate" : 1.0,
          "subscriberPrepaidPackageQty" : 0,
          "lac" : 12361,
          "cellId" : 115609386,
          "rat" : "4G - LTE",
          "imei" : "354647888013844",
          "upBitrate" : 0,
          "downBitrate" : 0,
          "qci" : 0,
          "apn" : "internet.emt.ee",
          "imsiPrefix" : 24801,
          "sponsorImsi" : 248010416000008,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 18037,
          "sessionId" : "38338685-1655377272",
          "usageDateUtc" : "2022-06-16T11:01:39",
          "usageType" : 40,
          "accountId" : 22,
          "accountName" : "Unknown - 22",
          "resellerId" : 7,
          "resellerName" : "Sparks Test",
          "mcc" : 250,
          "country" : "Russian Federation",
          "countryAlpha2" : "ru",
          "operator" : "PJSC Mobile TeleSystems MTS",
          "mnc" : 1,
          "quantity" : 5,
          "resellerCost" : 0.0,
          "resellerPlanId" : 4,
          "resellerPlanRuleId" : 19,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.0,
          "subscriberPlanId" : 4,
          "subscriberPlanRuleId" : 19,
          "subscriberCurrencyId" : 1,
          "subscriberConvertRate" : 1.0,
          "subscriberPrepaidPackageQty" : 0,
          "otherPartyNumber" : "79811564198",
          "imsiPrefix" : 24801,
          "sponsorImsi" : 248010416000008,
          "accountChargeEntity" : false
        }, {
          "subscriberId" : 18037,
          "sessionId" : "38338685-1655377272",
          "usageDateUtc" : "2022-06-16T11:01:39",
          "usageType" : 1,
          "accountId" : 22,
          "accountName" : "Unknown - 22",
          "resellerId" : 7,
          "resellerName" : "Sparks Test",
          "mcc" : 250,
          "country" : "Russian Federation",
          "countryAlpha2" : "ru",
          "operator" : "PJSC Mobile TeleSystems MTS",
          "mnc" : 1,
          "quantity" : 60,
          "resellerCost" : 0.42075,
          "resellerPlanId" : 400,
          "resellerPlanRuleId" : 1564,
          "resellerCurrencyId" : 1,
          "resellerConvertRate" : 1.0,
          "resellerPrepaidPackageQty" : 0,
          "subscriberCost" : 0.42075,
          "subscriberPlanId" : 400,
          "subscriberPlanRuleId" : 1564,
          "subscriberCurrencyId" : 1,
          "subscriberConvertRate" : 1.0,
          "subscriberPrepaidPackageQty" : 0,
          "otherPartyNumber" : "3726503944",
          "imsiPrefix" : 24801,
          "sponsorImsi" : 248010416000008,
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
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "period" : {
      "start" : "2023-09-08",
      "end" : "2023-09-03"
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


### 5.2.3 By ICCID
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "period" : {
      "start" : "2023-09-08",
      "end" : "2023-09-03"
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


### 5.2.4 By MSISDN
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "period" : {
      "start" : "2023-09-08",
      "end" : "2023-09-03"
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


### 5.2.5 By multi imsi
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "period" : {
      "start" : "2023-09-08",
      "end" : "2023-09-03"
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


### 5.2.6 By Activation code
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "period" : {
      "start" : "2023-09-08",
      "end" : "2023-09-03"
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
| 13 | OPERATION_IMPOSSIBLE |

