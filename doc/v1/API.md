## [1 Reseller](#11-listreselleraccount)

[1.1 listResellerAccount](#11-listreselleraccount)

[1.2 modifyAccountBalance](#12-modifyaccountbalance)

[1.3 modifyResellerBalance](#13-modifyresellerbalance)

[1.4 getResellerInfo](#14-getresellerinfo)

[1.5 esimStatusPerAccount](#15-esimstatusperaccount)

[1.6 listSponsor](#16-listsponsor)

[1.7 listSteeringList](#17-liststeeringlist)

## [2 Subscriber](#21-getsinglesubscriber)

[2.1 getSingleSubscriber](#21-getsinglesubscriber)

[2.2 listSubscriber](#22-listsubscriber)

[2.3 affectSubscriberRealPhoneNumber](#23-affectsubscriberrealphonenumber)

[2.4 affectSubscriberFakePhoneNumber](#24-affectsubscriberfakephonenumber)

[2.5 getSimProviderStatus](#25-getsimproviderstatus)

[2.6 modifySubscriberBalance](#26-modifysubscriberbalance)

[2.7 hlrSetBitrate](#27-hlrsetbitrate)

[2.8 hlrGetBitrate](#28-hlrgetbitrate)

[2.9 moveSubscriberRangeToAccount](#29-movesubscriberrangetoaccount)

[2.10 modifySubscriberContactInfo](#210-modifysubscribercontactinfo)

[2.11 modifySubscriberStatus](#211-modifysubscriberstatus)

[2.12 setSubscriberTrafficRestrictions](#212-setsubscribertrafficrestrictions)

[2.13 modifySubscriberSteeringList](#213-modifysubscribersteeringlist)

[2.14 pushSteeringToSubs](#214-pushsteeringtosubs)

[2.15 cleanSubscriberAllPackages](#215-cleansubscriberallpackages)

[2.16 resetSubsGzCounter](#216-resetsubsgzcounter)

[2.17 getSubscriberLocation](#217-getsubscriberlocation)

[2.18 getSubscriberLocationByCellId](#218-getsubscriberlocationbycellid)

## [3 Subscriber prepaid packages](#31-affectpackagetosubscriber)

[3.1 affectPackageToSubscriber](#31-affectpackagetosubscriber)

[3.2 affectRecurringPackageToSubscriber](#32-affectrecurringpackagetosubscriber)

[3.3 listSubscriberPrepaidPackages](#33-listsubscriberprepaidpackages)

[3.4 modifySubscriberPrepaidPackageLimits](#34-modifysubscriberprepaidpackagelimits)

[3.5 modifySubscriberPrepaidPackageExpDate](#35-modifysubscriberprepaidpackageexpdate)

[3.6 modifySubscriberPrepaidPackageStatus](#36-modifysubscriberprepaidpackagestatus)

[3.7 stopResumeSubsRecurringPackage](#37-stopresumesubsrecurringpackage)

[3.8 deleteSubscriberPackage](#38-deletesubscriberpackage)

## [4 Prepaid package template](#41-listprepaidpackagetemplate)

[4.1 listPrepaidPackageTemplate](#41-listprepaidpackagetemplate)

[4.2 listLocationZoneElement](#42-listlocationzoneelement)

[4.3 listDestinationListPrefix](#43-listdestinationlistprefix)

[4.4 listDetailedLocationZone](#44-listdetailedlocationzone)

[4.5 listDetailedDestinationList](#45-listdetaileddestinationlist)

[4.6 createPrepaidPackageTemplate](#46-createprepaidpackagetemplate)

[4.7 modifyPPTCore](#47-modifypptcore)

[4.8 modifyPPTRecurring](#48-modifypptrecurring)

[4.9 modifyPPTThrottling](#49-modifypptthrottling)

## [5 Tariff](#51-listresellertariff)

[5.1 listResellerTariff](#51-listresellertariff)

[5.2 listSubscriberTariff](#52-listsubscribertariff)

[5.3 listTariffRule](#53-listtariffrule)

[5.4 getCustomerTariff](#54-getcustomertariff)

## [6 Statistics](#61-getsubscriberactiveperiod)

[6.1 getSubscriberActivePeriod](#61-getsubscriberactiveperiod)

[6.2 subscriberUsageOverPeriod](#62-subscriberusageoverperiod)

[6.3 subscriberNetworkEventsOverPeriod](#63-subscribernetworkeventsoverperiod)

## [7 SMS](#71-sendmtsms)

[7.1 sendMtSms](#71-sendmtsms)

## [8 Network profile](#81-listnetworkprofile)

[8.1 listNetworkProfile](#81-listnetworkprofile)

[8.2 createLocationZone](#82-createlocationzone)

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
      "name" : "PDEL Reseller",
      "account" : [ {
        "id" : 4,
        "name" : "PDEL - Second account",
        "balance" : 10925.289088984377,
        "packageOnly" : false,
        "steeringListId" : 1
      }, {
        "id" : 7,
        "name" : "PDEL - Subs X",
        "balance" : 1000.0,
        "packageOnly" : false
      }, {
        "id" : 37,
        "name" : "TestSubscribers",
        "balance" : 197.80718309495325,
        "packageOnly" : false
      }, {
        "id" : 55,
        "name" : "FUT",
        "balance" : 70.06,
        "packageOnly" : false
      }, {
        "id" : 150,
        "name" : "PDEL Pack and Balance account",
        "balance" : 9940.0,
        "packageOnly" : false
      }, {
        "id" : 151,
        "name" : "PDEL - Package only",
        "balance" : 0.0,
        "packageOnly" : true
      } ]
    }, {
      "id" : 10,
      "name" : "PDEL Reseller 3",
      "account" : [ {
        "id" : 140,
        "name" : "Test dev account name 2",
        "balance" : 0.0,
        "packageOnly" : true
      }, {
        "id" : 141,
        "name" : "Test dev account name 3",
        "balance" : 100.0,
        "packageOnly" : true
      }, {
        "id" : 147,
        "name" : "PDEL 3 Pack_only_ACC",
        "balance" : 0.0,
        "packageOnly" : true
      }, {
        "id" : 148,
        "name" : "PDEL 3 Pack_And_Balance",
        "balance" : 100.0,
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
    }, {
      "id" : 65,
      "name" : "Denis Test Reseller",
      "account" : [ {
        "id" : 142,
        "name" : "Denis Res Subs account",
        "balance" : 0.0,
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
        "packageOnly" : false,
        "steeringListId" : 1
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
## 1.3 modifyResellerBalance

### Description
This request can be used to adapt the balance of reseller. The balance can either:
- Be adapted: You can add or remove a certain amount from the balance. The amount you need to provide in the request will be added to the current balance.  You can provide a negative amount and the balance will be decreased. Please note that balance  cannot become negative, in such a case the balance will be set to 0.
- Set to a new value: In this case you provide the new amount you want to set the balance to.

This request is logged in the system DB and you can see them in the UI, in the `Account` -> `Transaction` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|resellerId|Mandatory|The ID of the reseller to modify balance|
|type|Mandatory|Transaction type|
|amount|Mandatory|The amount to add to the current balance|
|setBalance|Optional|true => balance will be set to provided amount, false => balance will be adapted|
|description|Optional|A description giving information about the reason of this balance adjustment|


### 1.3.1 Update balance
#### Request
```json
{
  "modifyResellerBalance" : {
    "resellerId" : 1,
    "type" : "Wire",
    "amount" : 123.45,
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
### 1.3.2 Set balance
#### Request
```json
{
  "modifyResellerBalance" : {
    "resellerId" : 1,
    "type" : "Wire",
    "amount" : 123.45,
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
## 1.4 getResellerInfo

### Description
This request can be used to retrieve the reseller info.

The reseller ID in the request if optional. If no ID is provided in the request, the system will return
the reseller owning the token provided in the URL. If the reseller ID is provided in the request, the system
will return the reseller identified by the request ID.


### Request
```json
{
  "getResellerInfo" : {
    "id" : 111
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "getResellerInfo" : {
    "id" : 1,
    "name" : "PDEL Reseller",
    "parentId" : -1,
    "balance" : "8870,59",
    "cdrFolder" : "pdel_tap",
    "trafficInfo" : {
      "relayGy" : true,
      "relayCallSms" : false,
      "relayLU" : false,
      "relayVoIP" : false
    },
    "chargingInfo" : {
      "mobilePlan" : {
        "id" : 1,
        "name" : "PDEL - ResellerAccount"
      },
      "voipPlan" : {
        "id" : 1,
        "name" : "PDEL - VOiP Plan 1"
      },
      "CallPackageUseSingleCounter" : true,
      "voipFree" : false
    },
    "contactInfo" : {
      "contactName" : "Denis",
      "city" : "Bat Yam",
      "state" : "Israel",
      "country" : "Israel"
    }
  }
}
```
## 1.5 esimStatusPerAccount

### Description
This request can be used to retrieve the status of your eSIMs per account. You can retrieve the status
of your eSIMs for a specific account, or for all the accounts of a specific reseller.

The answer contains a list of account. For each account, you have a list of sponsor (for which you have eSIMs).
For each sponsor, you have a list of status (`Free` or `Affected`) with the count of eSIM for the status.

Status `Free` means that the eSIM is still available for a user. Status `Affected` means that the eSIM
has already been affected to a user.


### 1.5.1 For a specific account
#### Request
```json
{
  "esimStatusPerAccount" : {
    "accountId" : 222
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
  "esimStatusPerAccount" : {
    "account" : [ {
      "sponsor" : [ {
        "id" : 101,
        "name" : "Sponsor ABC",
        "esim" : {
          "status" : [ {
            "statusNum" : 0,
            "statusStr" : "Free",
            "count" : 100
          }, {
            "statusNum" : 2,
            "statusStr" : "Affected",
            "count" : 10
          } ]
        }
      } ],
      "id" : 222,
      "name" : "My account XYZ"
    } ]
  }
}
```
### 1.5.2 All accounts of a specific reseller
#### Request
```json
{
  "esimStatusPerAccount" : {
    "resellerId" : 111
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
  "esimStatusPerAccount" : {
    "account" : [ {
      "sponsor" : [ {
        "id" : 101,
        "name" : "Sponsor ABC",
        "esim" : {
          "status" : [ {
            "statusNum" : 0,
            "statusStr" : "Free",
            "count" : 100
          }, {
            "statusNum" : 2,
            "statusStr" : "Affected",
            "count" : 10
          } ]
        }
      } ],
      "id" : 222,
      "name" : "My account XYZ"
    } ]
  }
}
```
## 1.6 listSponsor

### Description
This request can be used to list the different sponsors configured for a reseller.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|listSponsor|Mandatory|The ID of the reseller for which to list the sponsor(s).|


### Request
```json
{
  "listSponsor" : 12
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSponsor" : {
    "sponsor" : [ {
      "id" : 1,
      "prefix" : 11122,
      "name" : "SP01"
    }, {
      "id" : 2,
      "prefix" : 33322,
      "name" : "SP02"
    } ]
  }
}
```
## 1.7 listSteeringList

### Description
This request can be used to list the different steering list of a reseller.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|listSteeringList|Mandatory|The ID of the reseller for which to list the steering list(s).|


### Request
```json
{
  "listSteeringList" : 12
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listSteeringList" : [ {
    "id" : 1,
    "resellerId" : 12,
    "name" : "Steering list 1"
  }, {
    "id" : 2,
    "resellerId" : 12,
    "name" : "Steering list 2"
  }, {
    "id" : 3,
    "resellerId" : 12,
    "name" : "Steering list 3"
  } ]
}
```
### Remark(s)

- The numeric value in the request is the reseller ID


# 2. Subscriber
## 2.1 getSingleSubscriber

### Description
This request can be used to search for a specific subscriber. The subscriber can be found via its:
- IMSI
- ICCID
- MSISDN
- eSIM activation code
- OCS internal ID

Remarks when searching with IMSI, ICCID or MSISDN:
- Unlike the `listSubscriber` you must provide the exact value, not a prefix.
- Unlike the `listSubscriber` the system will search only the currently active object (IMSI, ICCID or MSISDN). If you search by MSISDN, the provided MSISDN must be the currently active MSISDN for the subscriber. If you provide the MSISDN that was active in the past, but not anymore, the system will not find your subscriber.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|imsi|Optional|IMSI of the subscribers to find.|
|iccid|Optional|ICCID of the subscribers to find.|
|msisdn|Optional|MSISDN of the subscribers to find.|
|subscriberId|Optional|The ID of the subscriber.|
|activationCode|Optional|The eSIM activation code. The request will return the subscriber having the eSIM having with this activation code|
|withSimInfo|Optional|If set to `true`, the eSIM info of the subscriber will be returned. If not present, default value is `true`|
|onlySubsInfo|Optional|If set to `true`, you will get the basic info of the subscriber. If set to false `false`, you will get additional info like: imsi history, msisdn history, status history. Default value is `false`|
|withGzCounter|Optional|If set to `true`, the Green Zone counter of the subscriber will be returned. Default value is `false`|


### 2.1.1 IMSI
#### Request
```json
{
  "getSingleSubscriber" : {
    "imsi" : "9999900000",
    "withGzCounter" : true
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
  "getSingleSubscriber" : {
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
    "networkInfo" : {
      "subscriberid" : 21046,
      "time" : "2025-08-08T10:11:21.624236",
      "lastMcc" : 222,
      "lastMnc" : 99,
      "lastCellId" : 123456,
      "lastLac" : 456,
      "lastImei" : "789456123",
      "lastRat" : "3G - UTRAN"
    },
    "greenZoneCounter" : {
      "subscriberId" : 4,
      "volumeOnGZ" : 0,
      "lastResetDate" : "2024-11-11T11:05:48",
      "lastUpdateDate" : "2024-10-25T09:03:44"
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
    "lastMnc" : 50,
    "steeringListId" : 1,
    "throttlingLimit" : 128
  }
}
```
#### Remark(s)

- `networkInfo` is optional. If the subscriber has not been active yet, this object will be null


### 2.1.2 ICCID
#### Request
```json
{
  "getSingleSubscriber" : {
    "iccid" : "9999900017170",
    "withSimInfo" : true,
    "onlySubsInfo" : true
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

- See answer from previous case


### 2.1.3 MSISDN
#### Request
```json
{
  "getSingleSubscriber" : {
    "msisdn" : "1234567",
    "withSimInfo" : false,
    "onlySubsInfo" : false,
    "withGzCounter" : false
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

- See answer from previous case


### 2.1.4 eSIM activation code
#### Request
```json
{
  "getSingleSubscriber" : {
    "activationCode" : "activation code",
    "withSimInfo" : true,
    "onlySubsInfo" : false,
    "withGzCounter" : true
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

- The request here is searching for the exact activation, hence the request will always return 0 or 1 subscriber/sim
- See answer from previous case


### 2.1.5 Subscriber Id
#### Request
```json
{
  "getSingleSubscriber" : {
    "subscriberId" : 4,
    "withSimInfo" : false,
    "onlySubsInfo" : true,
    "withGzCounter" : true
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

- See answer from previous case


## 2.2 listSubscriber

### Description
This request can be used to search for subscriber. You can search for subscribers by:
- IMSI prefix
- ICCID prefix
- Account
- eSIM activation code


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|imsi|Optional|IMSI prefix for the subscribers to list. Minimum 10 digits long|
|iccid|Optional|ICCID prefix for the subscribers to list. Minimum 13 digits long|
|msisdn|Optional|MSISDN prefix for the subscribers to list. Minimum 7 digits long|
|accountId|Optional|The ID of the account. The request will return the list of all the subscriber attached to this account|
|activationCode|Optional|The eSIM activation code. The request will return the subscriber with the eSIM having this activation code|


### 2.2.1 IMSI prefix
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
### 2.2.2 ICCID prefix
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
### 2.2.3 MSISDN prefix
#### Request
```json
{
  "listSubscriber" : {
    "msisdnPrefix" : "1234567"
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
### 2.2.4 Account Id
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
### 2.2.5 eSIM activation code
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
      "lastMnc" : 50,
      "steeringListId" : 1,
      "throttlingLimit" : 128
    } ],
    "hasMore" : false,
    "nbFound" : 1
  }
}
```
#### Remark(s)

- The request here is searching for the exact activation, hence the request will always return 0 or 1 subscriber/sim


## 2.3 affectSubscriberRealPhoneNumber

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


### 2.3.1 By subscriber ID
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
### 2.3.2 By IMSI
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

- To get complete answer description, please refer to first example.


### 2.3.3 By ICCID
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

- To get complete answer description, please refer to first example.


### 2.3.4 By MSISDN
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

- To get complete answer description, please refer to first example.


### 2.3.5 By multi imsi
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

- To get complete answer description, please refer to first example.


### 2.3.6 By Activation code
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.4 affectSubscriberFakePhoneNumber

### Description
This request can be used to re-affect a subscriber its fake phone number.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### 2.4.1 By subscriber ID
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
### 2.4.2 By IMSI
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

- To get complete answer description, please refer to first example.


### 2.4.3 By ICCID
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

- To get complete answer description, please refer to first example.


### 2.4.4 By MSISDN
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

- To get complete answer description, please refer to first example.


### 2.4.5 By multi imsi
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

- To get complete answer description, please refer to first example.


### 2.4.6 By Activation code
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.5 getSimProviderStatus

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


## 2.6 modifySubscriberBalance

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


### 2.6.1 Update balance
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
### 2.6.2 Set balance
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
## 2.7 hlrSetBitrate

### Description
This request is part of the throttling API.

It will set a new bandwidth limitation for the subscriber identified by the IMSI.

Possible values for the `limit` field:
- KB_32: User will be limited 32 Kbit/sec
- KB_64: User will be limited 64 Kbit/sec
- KB_128: User will be limited 128 Kbit/sec
- KB_256: User will be limited 256 Kbit/sec
- KB_384: User will be limited 384 Kbit/sec
- KB_512: User will be limited 512 Kbit/sec
- KB_1024: User will be limited 1024 Kbit/sec
- KB_3072: User will be limited 3072 Kbit/sec
- KB_5120: User will be limited 5120 Kbit/sec
- KB_7680: User will be limited 7680 Kbit/sec
- KB_10240: User will be limited 10240 Kbit/sec
- KB_20480: User will be limited 20480 Kbit/sec
- UNLIMITED: User will not be limited.


### Request
```json
{
  "hlrSetBitrate" : {
    "imsi" : "123456789",
    "limit" : "KB_512"
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
## 2.8 hlrGetBitrate

### Description
This request is part of the throttling API.

It retrieves the current limitation of the subscriber in terms of data bandwidth.


### Request
```json
{
  "hlrGetBitrate" : {
    "imsi" : "123456789"
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "hlrGetBitrate" : "UNLIMITED"
}
```
## 2.9 moveSubscriberRangeToAccount

### Description
This method can be used to move a range a subscribers from one account to another account. The range of
subscriber can be either a range of IMSI, or a range of ICCID.

In this version, the move is restricted between accounts of the same reseller. If you need to move subscribers
between accounts of different resellers, please use the version 2 of this request.

If you move subscribers to a different reseller, all the moved subscribers will lose their prepaid
packages. Indeed, location zone (that is attached to each and every packages) from reseller A, is not
visible in reseller B. Meaning packages from reseller A are not visible in reseller B, so no need to
keep them.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|rangeType|Mandatory|Indicate the type of range. Possible values: `IMSI`, `ICCID`.|
|rangeStart|Mandatory|IMSI or ICCID of the first subscriber of the range to move|
|rangeEnd|Mandatory|IMSI or ICCID of the last subscriber of the range to move|
|srcAccountId|Mandatory|Current account of the subscriber to move|
|destAccount|Mandatory|New account for the subscriber to move|


### Outputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|moveSubscriberRangeToAccount|Mandatory|The number of subscriber that has been moved.|


### 2.9.1 IMSI range
#### Request
```json
{
  "moveSubscriberRangeToAccount" : {
    "rangeType" : "IMSI",
    "rangeStart" : "200010416000001",
    "rangeEnd" : "2000104160000010",
    "srcAccountId" : 10,
    "destAccount" : 15
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
  "moveSubscriberRangeToAccount" : 4
}
```
### 2.9.2 ICCID range
#### Request
```json
{
  "moveSubscriberRangeToAccount" : {
    "rangeType" : "ICCID",
    "rangeStart" : "893720000000000001",
    "rangeEnd" : "893720000000000010",
    "srcAccountId" : 10,
    "destAccount" : 15
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
  "moveSubscriberRangeToAccount" : 4
}
```
## 2.10 modifySubscriberContactInfo

### Description
This request can be used to adapt the subscriber contact info.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID


### 2.10.1 By subscriber ID
#### Request
```json
{
  "modifySubscriberContactInfo" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "name" : "optional name",
    "phone" : "optional phone number",
    "mail" : "optional mail",
    "company" : "optional company"
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
### 2.10.2 By IMSI
#### Request
```json
{
  "modifySubscriberContactInfo" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "name" : "optional name",
    "mail" : "optional mail"
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
### 2.10.3 By ICCID
#### Request
```json
{
  "modifySubscriberContactInfo" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "phone" : "optional phone number",
    "company" : "optional company"
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
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.11 modifySubscriberStatus

### Description
This request can be used to change the status of a subscriber.

Only subscribers with the `ACTIVE` status can consume data, send/receive calls and SMS.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code

The possible values for the new status are:
- `ACTIVE`
- `INACTIVE`
- `DISCONNECTED`
- `SUSPENDED`
- `END_OF_LIFE`: This status is final. Once in this status, the subscriber can ONLY be re-activated via the OCS UI. No request in the API has the ability to re-activate a subscriber in this status. The following actions are not permitted on a subscriber in this status:
   - Change status (but still permitted in the UI)
   - Affect prepaid package
   - Affect real phone number
   - Change throttling
   - Change authorized traffic
   - Push steering to subscriber
   - Send SMS


### 2.11.1 By subscriber ID
#### Request
```json
{
  "modifySubscriberStatus" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "newStatus" : "ACTIVE"
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
### 2.11.2 By IMSI
#### Request
```json
{
  "modifySubscriberStatus" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "newStatus" : "INACTIVE"
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

- To get complete answer description, please refer to first example.


### 2.11.3 By ICCID
#### Request
```json
{
  "modifySubscriberStatus" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "newStatus" : "SUSPENDED"
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

- To get complete answer description, please refer to first example.


### 2.11.4 By MSISDN
#### Request
```json
{
  "modifySubscriberStatus" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "newStatus" : "INACTIVE"
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

- To get complete answer description, please refer to first example.


### 2.11.5 By multi imsi
#### Request
```json
{
  "modifySubscriberStatus" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "newStatus" : "END_OF_LIFE"
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

- To get complete answer description, please refer to first example.


### 2.11.6 By Activation code
#### Request
```json
{
  "modifySubscriberStatus" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "newStatus" : "DISCONNECTED"
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.12 setSubscriberTrafficRestrictions

### Description
This request can be used to configure the traffic types thar are allowed for a subscriber: Data,
MOC, MTC and SMS-MO. Please note that SMS-MT is always allowed.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|subscriber|Mandatory|Identifier of the subscriber,  see `Subscriber identifiers` in [OcsObjects.md](OcsObjects.md).|
|dataAllowed|Mandatory|Indicates if data is allowed for the subscriber.|
|mocAllowed|Mandatory|Indicates if MOC are allowed for the subscriber.|
|mtcAllowed|Mandatory|Indicates if MTC are allowed for the subscriber.|
|smsMoAllowed|Mandatory|Indicates if SMS-MO are allowed for the subscriber.|


### 2.12.1 By subscriber ID
#### Request
```json
{
  "setSubscriberTrafficRestrictions" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "dataAllowed" : true,
    "mocAllowed" : false,
    "mtcAllowed" : false,
    "smsMoAllowed" : true
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
### 2.12.2 By IMSI
#### Request
```json
{
  "setSubscriberTrafficRestrictions" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "dataAllowed" : true,
    "mocAllowed" : true,
    "mtcAllowed" : true,
    "smsMoAllowed" : true
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

- To get complete answer description, please refer to first example.


### 2.12.3 By ICCID
#### Request
```json
{
  "setSubscriberTrafficRestrictions" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "dataAllowed" : true,
    "mocAllowed" : false,
    "mtcAllowed" : true,
    "smsMoAllowed" : true
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

- To get complete answer description, please refer to first example.


### 2.12.4 By MSISDN
#### Request
```json
{
  "setSubscriberTrafficRestrictions" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "dataAllowed" : true,
    "mocAllowed" : true,
    "mtcAllowed" : false,
    "smsMoAllowed" : true
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

- To get complete answer description, please refer to first example.


### 2.12.5 By multi imsi
#### Request
```json
{
  "setSubscriberTrafficRestrictions" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "dataAllowed" : true,
    "mocAllowed" : false,
    "mtcAllowed" : true,
    "smsMoAllowed" : false
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

- To get complete answer description, please refer to first example.


### 2.12.6 By Activation code
#### Request
```json
{
  "setSubscriberTrafficRestrictions" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "dataAllowed" : false,
    "mocAllowed" : true,
    "mtcAllowed" : true,
    "smsMoAllowed" : true
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.13 modifySubscriberSteeringList

### Description
This request can be used to change or remove the steering list of the subscriber.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|subscriber|Mandatory|Identifier of the subscriber, see `Subscriber identifiers` in [OcsObjects.md](OcsObjects.md).|
|steeringListId|Optional|The new steering list for the subscriber. If none provided (null), the current list will be removed.|


### 2.13.1 By subscriber ID
#### Request
```json
{
  "modifySubscriberSteeringList" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "steeringListId" : 123
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
### 2.13.2 By IMSI
#### Request
```json
{
  "modifySubscriberSteeringList" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "steeringListId" : 123
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
### 2.13.3 By ICCID
#### Request
```json
{
  "modifySubscriberSteeringList" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "steeringListId" : 123
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
### 2.13.4 By MSISDN
#### Request
```json
{
  "modifySubscriberSteeringList" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "steeringListId" : 123
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
### 2.13.5 By multi imsi
#### Request
```json
{
  "modifySubscriberSteeringList" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "steeringListId" : 123
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
### 2.13.6 By Activation code
#### Request
```json
{
  "modifySubscriberSteeringList" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "steeringListId" : 123
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
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.14 pushSteeringToSubs

### Description
This request can be used to push the OPLMN list to the phone of the subscriber via OTA. You just need
to provide the ID of the subscriber, the system will find the current country of the subscriber,
build the OPLMN list for this country, and send it to the phone of the subscriber via OTA SMS.

This request can be used after a modification has been brought to a steering list, of if you changed
the steering list of subscriber, and you need to push it right away.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### 2.14.1 By subscriber ID
#### Request
```json
{
  "pushSteeringToSubs" : {
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
### 2.14.2 By IMSI
#### Request
```json
{
  "pushSteeringToSubs" : {
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
### 2.14.3 By ICCID
#### Request
```json
{
  "pushSteeringToSubs" : {
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
### 2.14.4 By MSISDN
#### Request
```json
{
  "pushSteeringToSubs" : {
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
### 2.14.5 By multi imsi
#### Request
```json
{
  "pushSteeringToSubs" : {
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
### 2.14.6 By Activation code
#### Request
```json
{
  "pushSteeringToSubs" : {
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
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.15 cleanSubscriberAllPackages

### Description
This request can be used to clean ALL the prepaid package AND ALL the recurring packages.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code


### 2.15.1 By subscriber ID
#### Request
```json
{
  "cleanSubscriberAllPackages" : {
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
### 2.15.2 By IMSI
#### Request
```json
{
  "cleanSubscriberAllPackages" : {
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
### 2.15.3 By ICCID
#### Request
```json
{
  "cleanSubscriberAllPackages" : {
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
### 2.15.4 By MSISDN
#### Request
```json
{
  "cleanSubscriberAllPackages" : {
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
### 2.15.5 By multi imsi
#### Request
```json
{
  "cleanSubscriberAllPackages" : {
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
### 2.15.6 By Activation code
#### Request
```json
{
  "cleanSubscriberAllPackages" : {
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
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.16 resetSubsGzCounter

### Description
This request can be used to reset the Green Zone counter of a subscriber.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code

In the answer you will get the counter with the new values.


### 2.16.1 By subscriber ID
#### Request
```json
{
  "resetSubsGzCounter" : {
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
  "resetSubsGzCounter" : {
    "subscriberId" : 4,
    "volumeOnGZ" : 123456,
    "lastResetDate" : "2025-08-08T08:11:21.627545",
    "lastUpdateDate" : "2025-08-07T21:05:21.627554"
  }
}
```
### 2.16.2 By IMSI
#### Request
```json
{
  "resetSubsGzCounter" : {
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
  "resetSubsGzCounter" : {
    "subscriberId" : 4,
    "volumeOnGZ" : 123456,
    "lastResetDate" : "2025-08-08T08:11:21.627545",
    "lastUpdateDate" : "2025-08-07T21:05:21.627554"
  }
}
```
### 2.16.3 By ICCID
#### Request
```json
{
  "resetSubsGzCounter" : {
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
  "resetSubsGzCounter" : {
    "subscriberId" : 4,
    "volumeOnGZ" : 123456,
    "lastResetDate" : "2025-08-08T08:11:21.627545",
    "lastUpdateDate" : "2025-08-07T21:05:21.627554"
  }
}
```
### 2.16.4 By MSISDN
#### Request
```json
{
  "resetSubsGzCounter" : {
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
  "resetSubsGzCounter" : {
    "subscriberId" : 4,
    "volumeOnGZ" : 123456,
    "lastResetDate" : "2025-08-08T08:11:21.627545",
    "lastUpdateDate" : "2025-08-07T21:05:21.627554"
  }
}
```
### 2.16.5 By multi imsi
#### Request
```json
{
  "resetSubsGzCounter" : {
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
  "resetSubsGzCounter" : {
    "subscriberId" : 4,
    "volumeOnGZ" : 123456,
    "lastResetDate" : "2025-08-08T08:11:21.627545",
    "lastUpdateDate" : "2025-08-07T21:05:21.627554"
  }
}
```
### 2.16.6 By Activation code
#### Request
```json
{
  "resetSubsGzCounter" : {
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
  "resetSubsGzCounter" : {
    "subscriberId" : 4,
    "volumeOnGZ" : 123456,
    "lastResetDate" : "2025-08-08T08:11:21.627545",
    "lastUpdateDate" : "2025-08-07T21:05:21.627554"
  }
}
```
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.
- In the answer, the volume is byte.


## 2.17 getSubscriberLocation

### Description
This request can be used to get the last known location of a subscriber based on the last known tower cell.

Please note that we cannot always provide the location:
- If we don't have any usages yet, for example the eSIM has not been activated yet.
- If we have usages, but we didn't receive the location information.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code

In the answer you will get latitude and longitude, accuracy in meters, and date and time (UTC+0) of our last known location (last time the subscriber was "seen" by our system).
The accuracy is the estimated median error in meters, i.e. the radius in a circle with 50% confidence level


### 2.17.1 By subscriber ID
#### Request
```json
{
  "getSubscriberLocation" : {
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
  "subscriberLocation" : {
    "latitude" : 47.447163,
    "longitude" : 8.55877,
    "accuracy" : 250,
    "dateTime" : "2025-08-07T10:11:21.627571"
  }
}
```
### 2.17.2 By IMSI
#### Request
```json
{
  "getSubscriberLocation" : {
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
  "subscriberLocation" : {
    "latitude" : 47.447163,
    "longitude" : 8.55877,
    "accuracy" : 250,
    "dateTime" : "2025-08-07T10:11:21.627571"
  }
}
```
### 2.17.3 By ICCID
#### Request
```json
{
  "getSubscriberLocation" : {
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
  "subscriberLocation" : {
    "latitude" : 47.447163,
    "longitude" : 8.55877,
    "accuracy" : 250,
    "dateTime" : "2025-08-07T10:11:21.627571"
  }
}
```
### 2.17.4 By MSISDN
#### Request
```json
{
  "getSubscriberLocation" : {
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
  "subscriberLocation" : {
    "latitude" : 47.447163,
    "longitude" : 8.55877,
    "accuracy" : 250,
    "dateTime" : "2025-08-07T10:11:21.627571"
  }
}
```
### 2.17.5 By multi imsi
#### Request
```json
{
  "getSubscriberLocation" : {
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
  "subscriberLocation" : {
    "latitude" : 47.447163,
    "longitude" : 8.55877,
    "accuracy" : 250,
    "dateTime" : "2025-08-07T10:11:21.627571"
  }
}
```
### 2.17.6 By Activation code
#### Request
```json
{
  "getSubscriberLocation" : {
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
  "subscriberLocation" : {
    "latitude" : 47.447163,
    "longitude" : 8.55877,
    "accuracy" : 250,
    "dateTime" : "2025-08-07T10:11:21.627571"
  }
}
```
### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 2.18 getSubscriberLocationByCellId

### Description
This request can be used to get location of a subscriber based on tower cell ID: radio type, mcc, mnc, lac, cell id.
Radio type should be one of: "2G", "3G", "4G", "5G", "NBIOT".

In the answer you will get latitude and longitude, accuracy in meters.
The accuracy is the estimated median error in meters, i.e. the radius in a circle with 50% confidence level


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|radioType|Mandatory|Possible values: '2G', '3G', '4G', '5G' and 'NB-IoT'.|
|mcc|Mandatory|Mobile country code.|
|mnc|Mandatory|Mobile network code.|
|lac|Mandatory|Location area code.|
|cellId|Optional|The tower cell Id. It's optional, but if not provided, the location will be very inaccurate.|


### Request
```json
{
  "getSubscriberLocationByCellId" : {
    "radioType" : "4G",
    "mcc" : 250,
    "mnc" : 99,
    "lac" : 9830,
    "cellId" : 79131751,
    "signalStrength" : -89
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "subscriberLocation" : {
    "latitude" : 46.54557,
    "longitude" : 48.620538,
    "accuracy" : 250
  }
}
```
# 3. Subscriber prepaid packages
## 3.1 affectPackageToSubscriber

### Description
This request can be used to affect a new prepaid package to a subscriber. The prepaid package
affected to the subscriber will be created based on the package template provided in the request
(you can get the list of template via request `listPrepaidPackageTemplate`).

Please note that this request will activate the subscriber, if it is not active yet. Meaning after
this request (successfully executed), the user can start using its prepaid package, no matter if it
was active or not before the request.

The subscriber (and its eSIM) can be provided in the request (see `subscriber`), then the system
will affect a new plan to the specified subscriber.

But instead of a subscriber, an account can be provided (see `accountForSubs`). In this case the system will search for
a free eSIM (and its subscriber) in the specified account. If a free eSIM is found, a new package
will be affected to its subscriber.

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
- No `activePeriod` nor `validityPeriod` for activation at first use: The start date and time will be the date and time of
  the first successful usage of the prepaid package template. The end date and time of the package will be
  the first successful usage date and time, plus the number of days for validity configured in the
  package template.


### 3.1.1 By subscriber ID
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "subscriberId" : 1000
    },
    "activePeriod" : {
      "start" : "2025-08-08T10:11:21.628464",
      "end" : "2025-09-07T10:11:21.628472"
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
### 3.1.2 By IMSI
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

- To get complete answer description, please refer to first example.


### 3.1.3 By ICCID
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

- To get complete answer description, please refer to first example.


### 3.1.4 By MSISDN
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

- To get complete answer description, please refer to first example.


### 3.1.5 By multi imsi
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

- To get complete answer description, please refer to first example.


### 3.1.6 By Activation code
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

- To get complete answer description, please refer to first example.


### 3.1.7 With account
#### Request
```json
{
  "affectPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "accountForSubs" : 40,
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 3.2 affectRecurringPackageToSubscriber

### Description
For a complete description of the recurring packages, please refer to OCS UI documentation.

This request can be used to affect a new recurring prepaid package to a subscriber. The subscriber
prepaid packages generated by the recurring package will be created based on the package template
provided in the request (you can get the list of template via request `listPrepaidPackageTemplate`).

The subscriber packages will start to be generated once the start time of the recurring package
is reached, or when the user will start consume units on this package (A.K.A activation at first use).
When creating the recurring package, you need to decide if you want the recurring to be active from
a certain time, or if you want it to be activated at first use.

The packages will not be created all at once, when using this request. The packages will
created 12 hours in advance with the following logic:
- Start time based package: if the start time, is within the next 12 hours,
the first package will be created immediately, and will be returned in the answer. If the start time is after
the next 12 hours, no package will be created.
- Activation at first use package: A first subscriber package is created immediately (returned
in the answer). This first package will be created with no start date and end date, so it will be
activated at first use. When this first subscriber package will be activated, the recurring package
will also be activated, and from that moment, the other subscriber packages will be created 12 hours
in advance.

Please note that this request will activate the subscriber, if it is not active yet. Meaning after
this request (successfully executed), the user can start using its prepaid package, as soon as the
package is available.

To identify the subscriber, you can use one of the following IDs:
- Subscriber ID
- IMSI
- ICCID
- MSISDN
- Multi IMSI
- Activation code

For monthly recurring packages, the packages will be created the same day in the month as the first
package of the recurring packages. Meaning if the first package is created the 3rd of a month, all
the other packages will be given to the user every 3rd of the month.

For monthly recurring packages, packages are granted the same day in the month. This mean that in
some case we might need to create packages with invalid start date. For example, if the Start time
is august 31, we cannot have a package starting the 31 of september. In the case, the package will
be create with the closest previous valid date, in our example, the 30 of september.



### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|packageTemplateId|Mandatory|ID of package template to use to create the recurring package instance.|
|subscriber|Mandatory|One of the subscriber identifier see `Subscriber identifiers` in [OcsObjects.md](OcsObjects.md)|
|startTimeUTC|Optional|Moment from which the subscriber packages will be created. If not provided, and `activationAtFirstUse` is `false`, current date and time will be used as default value.|
|activationAtFirstUse|Optional|Flag indicating if the package needs to be activated when the subscriber will start consuming the first units. If not provided, default value is `false`. If value is `true`, `startTimeUTC` cannot be provided.|


### 3.2.1 By subscriber ID
#### Request
```json
{
  "affectRecurringPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "subscriberId" : 1000
    },
    "startTimeUTC" : "2025-08-08T08:11:21",
    "activationAtFirstUse" : false
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
  "affectRecurringPackageToSubscriber" : {
    "packageInfo" : {
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
      "active" : true
    },
    "simInfo" : {
      "iccid" : "123",
      "smdpServer" : "serv",
      "activationCode" : "blah blah",
      "urlQrCode" : "LPA:1$serv$blah blah",
      "subscriberId" : 4,
      "esimId" : 64612,
      "subsPackageId" : 1042,
      "userSimName" : "PDEL"
    }
  }
}
```
#### Remark(s)

- `startTimeUTC` is optional. The date and time when the first package of the series will be available to the user. If not provided, the system will take the current date and time as start date.


### 3.2.2 By IMSI
#### Request
```json
{
  "affectRecurringPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "startTimeUTC" : "2025-08-08T08:11:21",
    "activationAtFirstUse" : false
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

- To get complete answer description, please refer to first example.


### 3.2.3 By ICCID
#### Request
```json
{
  "affectRecurringPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "activationAtFirstUse" : false
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

- To get complete answer description, please refer to first example.


### 3.2.4 By MSISDN
#### Request
```json
{
  "affectRecurringPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "activationAtFirstUse" : true
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

- To get complete answer description, please refer to first example.


### 3.2.5 By multi imsi
#### Request
```json
{
  "affectRecurringPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "startTimeUTC" : "2025-08-08T08:11:21",
    "activationAtFirstUse" : false
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

- To get complete answer description, please refer to first example.


### 3.2.6 By Activation code
#### Request
```json
{
  "affectRecurringPackageToSubscriber" : {
    "packageTemplateId" : 553,
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "activationAtFirstUse" : true
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 3.3 listSubscriberPrepaidPackages

### Description
This request can be used to list all the pre paid packages of a subscriber (if any).

_If you are using recurring packages, please use [version 2](..%2Fv2%2FAPI.md)_

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


### 3.3.1 By subscriber ID
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
### 3.3.2 By IMSI
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

- To get complete answer description, please refer to first example.


### 3.3.3 By ICCID
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

- To get complete answer description, please refer to first example.


### 3.3.4 By MSISDN
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

- To get complete answer description, please refer to first example.


### 3.3.5 By multi imsi
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

- To get complete answer description, please refer to first example.


### 3.3.6 By Activation code
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 3.4 modifySubscriberPrepaidPackageLimits

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
## 3.5 modifySubscriberPrepaidPackageExpDate

### Description
This request can be used to adapt the expiration date of a subscriber prepaid package.

This request is logged in the system DB and you can see them in the UI, in the `Subscriber prepaid package` -> `History` tab.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|packageId|Mandatory|The ID of the subscriber prepaid package to adapt.|
|newPeriod|Optional|The number of days between the start validity date and the new expiration date. You don't really need to update this value, but if you want to keep data consistent, provide the correct value.|
|newDateUtc|Mandatory|The new expiration date for the subscriber prepaid package.|


### Request
```json
{
  "modifySubscriberPrepaidPackageExpDate" : {
    "packageId" : 123,
    "newPeriod" : 45,
    "newDateUtc" : "2025-08-08T10:11:21"
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
## 3.6 modifySubscriberPrepaidPackageStatus

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
## 3.7 stopResumeSubsRecurringPackage

### Description
This request can be used to stop or resume a recurring package. If you stop a recurring package, the subscriber
will stop receiving packages for this recurring package. If you resume a stopped recurring package, the
subscriber will receive again its packages.

You can use this request to stop/resume:
1. A specific recurring package of a subscriber. In this case you need to provide the field `recurringId`.
2. All the recurring packages of a specific subscriber. In this case you need to provide the field `subscriberId`.
3. All the recurring packages, of all the subscriber, of a specific template. In this case you need to provide the field `templateId`.

Please note that to get the recurring packages of a subscriber, you need to use the [version 2](..%2Fv2%2FAPI.md) of the list subscriber prepaid packages request= `listSubscriberPrepaidPackages`.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|recurringId|Optional|The ID of the recurring package you want to stop/resume. You can find it in the answer of the `listSubscriberPrepaidPackages` ([version 2](..%2Fv2%2FAPI.md)): recurring[i].id|
|subscriberId|Optional|The ID of the subscriber for which you want to stop ALL recurring packages.|
|templateId|Optional|The ID of the template for which you want to to stop ALL the instances of ALL the subscribers.|
|active|Mandatory|Flag indicating if you to stop (active=false) or resume (active=true) the recurring package(s).|


### 3.7.1 With recurring package ID
#### Request
```json
{
  "stopResumeSubsRecurringPackage" : {
    "recurringId" : 4,
    "active" : false
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
### 3.7.2 With subscriber ID
#### Request
```json
{
  "stopResumeSubsRecurringPackage" : {
    "subscriberId" : 123456789,
    "active" : false
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
### 3.7.3 With package template ID
#### Request
```json
{
  "stopResumeSubsRecurringPackage" : {
    "templateId" : 123,
    "active" : true
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
## 3.8 deleteSubscriberPackage

### Description
This request can be used to delete a prepaid package of a subscriber.


### Request
```json
{
  "deleteSubscriberPackage" : 123
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
### Remark(s)

- The numeric value of the request is the prepais package ID


# 4. Prepaid package template
## 4.1 listPrepaidPackageTemplate

### Description
This request can be used to list your prepaid package templates. You have several keys to search the templates:
- Reseller: the request will return all the templates of the reseller.
- Location zone: the request wil return all templates linked to that particular location zone.
- Sponsor: The request will list all your templates linked to that particular sponsor.
- Template: By providing a template id you will retrieve this template.

You can also send the request without any search keys. In this case the request will return all your templates.


### 4.1.1 By template Id
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
### 4.1.2 By reseller
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
### 4.1.3 By sponsor
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


### 4.1.4 By location zone
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


### 4.1.5 By destination list
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


### 4.1.6 No search keys
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


## 4.2 listLocationZoneElement

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


## 4.3 listDestinationListPrefix

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


## 4.4 listDetailedLocationZone

### Description
This request can be used to list all the 'Location zone' of a reseller (customer). This request is returning the complete
list operator (including MCC-MNC and TADIGs) for each  zone.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|listDetailedLocationZone|Mandatory|ID of the reseller for which to list the location zones|


### Request
```json
{
  "listDetailedLocationZone" : 1
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listDetailedLocationZone" : [ {
    "zoneId" : 27,
    "zoneName" : "PDEL - Test eSIM",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "operators" : [ {
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
    }, {
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
    } ]
  }, {
    "zoneId" : 1121,
    "zoneName" : "TEST_LZ",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "operators" : [ {
      "networkId" : 769,
      "continent" : "Asia",
      "countryCode" : 7,
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
  } ]
}
```
### Remark(s)

- Note that if there no zone configured for an operator the `listDetailedLocationZone` is going to be null, not empty array


## 4.5 listDetailedDestinationList

### Description
This request can be used to list all the 'Destination list' of a reseller (customer). The request returns
the list of prefixes configured in each list.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|listDetailedDestinationList|Mandatory|ID of the reseller for which to list the destination list|


### Request
```json
{
  "listDetailedDestinationList" : 1
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listDetailedDestinationList" : [ {
    "listId" : 5,
    "listName" : "Denis Destination list",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "prefixes" : [ "665", "7" ]
  }, {
    "listId" : 6,
    "listName" : "Denis new List",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "prefixes" : [ "343" ]
  }, {
    "listId" : 7,
    "listName" : "dddd",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    }
  }, {
    "listId" : 11,
    "listName" : "Denis Super Destination",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "prefixes" : [ "346", "666" ]
  }, {
    "listId" : 12,
    "listName" : "Dest list 1",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "prefixes" : [ "12", "641" ]
  }, {
    "listId" : 14,
    "listName" : "PDEL Destination list",
    "reseller" : {
      "id" : 1,
      "name" : "PDEL Reseller"
    },
    "prefixes" : [ "113", "99" ]
  } ]
}
```
### Remark(s)

- Note that if there no list configured for an operator the `listDetailedDestinationList` is going to be null, not empty array


## 4.6 createPrepaidPackageTemplate

### Description
This request can be used to create a prepaid package template.

REMARK:
If reseller is configured to use a single counter for MOC and MTC for its packages, MOC counter `mocsecond` needs to contain
the value for MOC and MTC.

Please refer to OCS User guide ( available from OCS UI) for a full description of the recurring and throttling features.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|prepaidpackagetemplatename|Mandatory|The name of the template to create.|
|resellerid|Mandatory|ID of the reseller to which the template will belong.|
|locationzoneid|Mandatory|ID of the 'Location zone' for this template. See [listDetailedLocationZone](#37-listdetailedlocationzone).|
|destinationzoneid|Optional|ID of the 'Destination list' for this template. See [listDetailedDestinationList](#38-listdetaileddestinationlist).|
|databyte|Optional|Maximum volume for packages instantiated from this template.|
|mocsecond|Optional|Maximum MOC seconds for packages instantiated from this template.|
|mtcsecond|Optional|Maximum MTC seconds for packages instantiated from this template.|
|mosmsnumber|Optional|Maximum number of MO-SMS for packages instantiated from this template.|
|mtsmsnumber|Optional|Maximum number of MT-SMS for packages instantiated from this template.|
|perioddays|Mandatory|Duration (in days) of the validity period for packages instantiated from this template.|
|cost|Optional|Informative field you can use to store the price you're selling packages issued from this template.|
|throttlingActive|Mandatory|Indicates if the throttling feature is active for this template.|
|throttlingThreshold1Perc|Optional|First threshold for throttling, in percentage of the total volume of the package. See possible values in below remarks.|
|throttlingThreshold1Limit|Optional|Limit to apply when the subscriber is crossing the first threshold.|
|throttlingThreshold2Perc|Optional|Second threshold for throttling, in percentage of the total volume of the package. See possible values in below remarks.|
|throttlingThreshold2Limit|Optional|Limit to apply when the subscriber is crossing the second threshold.|
|throttlingErrorAction|Optional|What is happening to the package if the throttling request failed to reach the subscriber. Possible values are: 0=User can continue to use the template (no speed limitation), 1=Package is blocked and user cannot use it anymore.|
|recurring|Mandatory|Indicates if the recurring feature is active for this template.|
|nbOccurrence|Optional|Indicates the max number of package to give to the subscriber.|
|recurringPeriodicityType|Optional|Recurring periodicity type. Possible values: 0=Daily, 1=Weekly, 2=Monthly.|
|recurringPeriodicityFrequency|Optional|Along with `recurringPeriodicityType` will determine the frequency at which the subscriber will receive its packages. For example `recurringPeriodicityType`=`0` and `recurringPeriodicityFrequency`=`2`, the subscriber is going to receive a package every 2 days.|
|reportUnitsPreviousPackage|Optional|When creating a new package for a subscriber, indicated if the remaining units of the previous packages needs to be reported (added to the new packages).|


### Request
```json
{
  "createPrepaidPackageTemplate" : {
    "prepaidpackagetemplatename" : "Name",
    "resellerid" : 123,
    "locationzoneid" : 123,
    "destinationzoneid" : 123,
    "databyte" : 10000000,
    "mocsecond" : 60,
    "mtcsecond" : 90,
    "mosmsnumber" : 100,
    "mtsmsnumber" : 120,
    "perioddays" : 45,
    "cost" : 15.5,
    "throttlingActive" : true,
    "throttlingThreshold1Perc" : 70,
    "throttlingThreshold1Limit" : 256,
    "throttlingThreshold2Perc" : 90,
    "throttlingThreshold2Limit" : 128,
    "throttlingErrorAction" : 1,
    "recurring" : true,
    "nbOccurrence" : 12,
    "recurringPeriodicityType" : 2,
    "recurringPeriodicityFrequency" : 12,
    "reportUnitsPreviousPackage" : true
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "createPrepaidPackageTemplate" : {
    "rdbDestinationZones" : {
      "destinationzoneid" : 5,
      "destinationzonename" : "Denis Destination list"
    },
    "prepaidpackagetemplateid" : 9359,
    "prepaidpackagetemplatename" : "Name",
    "resellerid" : 1,
    "priority" : 1,
    "locationzoneid" : 27,
    "destinationzoneid" : 5,
    "databyte" : 10000000,
    "mocsecond" : 60,
    "mtcsecond" : 90,
    "mosmsnumber" : 100,
    "mtsmsnumber" : 120,
    "perioddays" : 45,
    "deleted" : false,
    "esimSponsor" : 102,
    "cost" : 15.5,
    "uiVisible" : false,
    "throttlingActive" : true,
    "throttlingThreshold1Perc" : 70,
    "throttlingThreshold1Limit" : 256,
    "throttlingThreshold2Perc" : 90,
    "throttlingThreshold2Limit" : 128,
    "throttlingErrorAction" : 1,
    "recurring" : true,
    "nbOccurrence" : 12,
    "recurringPeriodicityType" : 2,
    "recurringPeriodicityFrequency" : 12,
    "reportUnitsPreviousPackage" : true,
    "resellerName" : "PDEL Reseller",
    "sponsorName" : "SP02",
    "zone" : {
      "locationZoneId" : 27,
      "locationZoneName" : "PDEL - Test eSIM",
      "countryList" : [ {
        "continent" : "Europe",
        "countryId" : 21,
        "countryName" : "Belgium",
        "countryIso2" : "be",
        "countryCode" : 32
      }, {
        "continent" : "Europe",
        "countryId" : 100,
        "countryName" : "Italy",
        "countryIso2" : "it",
        "countryCode" : 39
      } ],
      "operatorList" : [ {
        "operId" : 477,
        "operatorName" : "H3G S p A ",
        "tadigList" : [ "ITAH3" ],
        "mccMncList" : [ "222-99" ],
        "countryId" : 100
      }, {
        "operId" : 79,
        "operatorName" : "Proximus PLC",
        "tadigList" : [ "BELTB" ],
        "mccMncList" : [ "206-01" ],
        "countryId" : 21
      } ]
    },
    "useSingleCounterForCall" : true
  }
}
```
### Remark(s)

- `throttlingThreshold1Perc` and `throttlingThreshold1Limit` are optional, but if one is set in the request, the other must be provided
- `throttlingThreshold2Perc` and `throttlingThreshold2Limit` are optional, but if one is set in the request, the other must be provided
- `throttlingErrorAction` is mandatory if `throttlingActive` is `true`
- Possible values for `throttlingThreshold1Limit` and `throttlingThreshold2Limit` in request, those are speed limitation in Kbit:
   - 128
   - 256
   - 384
   - 512
   - 1024
   - 3072
   - 5120
   - 7680
   - 10240
   - 20480

- If `recurring` is `true`, then `nbOccurrence`, `recurringPeriodicityType`, `recurringPeriodicityFrequency`, `reportUnitsPreviousPackage` are mandatory
- If `recurring` is `true`, `nbOccurrence` remains optional, but only for monthly recurring package template. If not provided, it means there won't be any stop the recurring package (infinite number of package will be given).


## 4.7 modifyPPTCore

### Description
This request can be used to modify a prepaid package template.

REMARK:
If reseller is configured to use a single counter for MOC and MTC for its packages, MOC counter `mocsecond` needs to contain
the value for MOC and MTC.

Please refer to OCS User guide ( available from OCS UI) for a full description of the recurring and throttling features.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|prepaidpackagetemplatename|Mandatory|The name of the template to create.|
|resellerid|Mandatory|ID of the reseller to which the template will belong.|
|locationzoneid|Mandatory|ID of the 'Location zone' for this template. See [listDetailedLocationZone](#37-listdetailedlocationzone).|
|destinationzoneid|Optional|ID of the 'Destination list' for this template. See [listDetailedDestinationList](#38-listdetaileddestinationlist).|
|databyte|Optional|Maximum volume for packages instantiated from this template.|
|mocsecond|Optional|Maximum MOC seconds for packages instantiated from this template.|
|mtcsecond|Optional|Maximum MTC seconds for packages instantiated from this template.|
|mosmsnumber|Optional|Maximum number of MO-SMS for packages instantiated from this template.|
|mtsmsnumber|Optional|Maximum number of MT-SMS for packages instantiated from this template.|
|perioddays|Mandatory|Duration (in days) of the validity period for packages instantiated from this template.|
|cost|Optional|Informative field you can use to store the price you're selling packages issued from this template.|
|changeSponsor|Optional|Must be present and `true` if you want to configure a location from another sponsor.|


### Request
```json
{
  "modifyPPTCore" : {
    "prepaidpackagetemplateid" : 123,
    "prepaidpackagetemplatename" : "Name",
    "resellerid" : 123,
    "locationzoneid" : 123,
    "destinationzoneid" : 123,
    "databyte" : 10000000,
    "mocsecond" : 60,
    "mtcsecond" : 90,
    "mosmsnumber" : 100,
    "mtsmsnumber" : 120,
    "perioddays" : 45,
    "esimSponsor" : 155,
    "cost" : 15.5,
    "changeSponsor" : true
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "modifyPrepaidPackageTemplate" : {
    "rdbDestinationZones" : {
      "destinationzoneid" : 5,
      "destinationzonename" : "Denis Destination list"
    },
    "prepaidpackagetemplateid" : 9359,
    "prepaidpackagetemplatename" : "Name 2",
    "resellerid" : 1,
    "priority" : 1,
    "locationzoneid" : 1121,
    "destinationzoneid" : 5,
    "databyte" : 100000000,
    "mocsecond" : 61,
    "mtcsecond" : 91,
    "mosmsnumber" : 101,
    "mtsmsnumber" : 1201,
    "perioddays" : 30,
    "deleted" : false,
    "cost" : 25.5,
    "uiVisible" : false,
    "throttlingActive" : true,
    "throttlingThreshold1Perc" : 75,
    "throttlingThreshold1Limit" : 128,
    "throttlingThreshold2Perc" : 95,
    "throttlingThreshold2Limit" : 256,
    "throttlingErrorAction" : 1,
    "recurring" : true,
    "nbOccurrence" : 15,
    "recurringPeriodicityType" : 1,
    "recurringPeriodicityFrequency" : 10,
    "reportUnitsPreviousPackage" : true,
    "resellerName" : "PDEL Reseller",
    "sponsorName" : "SP01",
    "zone" : {
      "locationZoneId" : 1121,
      "locationZoneName" : "TEST_LZ",
      "countryList" : [ {
        "continent" : "Asia",
        "countryId" : 168,
        "countryName" : "Russian Federation",
        "countryIso2" : "ru",
        "countryCode" : 7
      } ],
      "operatorList" : [ {
        "operId" : 769,
        "operatorName" : "OJSC MegaFon",
        "tadigList" : [ "RUSNW" ],
        "mccMncList" : [ "250-02" ],
        "countryId" : 168
      } ]
    },
    "useSingleCounterForCall" : false
  }
}
```
## 4.8 modifyPPTRecurring

### Description
This request can be used to modify the recurring configuration of a prepaid package template.

Please refer to OCS User guide ( available from OCS UI) for a full description of the recurring and throttling features.

Please note:
- If You de-activate "Recurring", the subscribers having instance of this template will stop receiving new packages.
- Modification of `recurringPeriodicityFrequency`, `recurringPeriodicityType` and `nbOccurrence` WILL NOT AFFECT subscribers having instance of this template.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|recurring|Mandatory|Indicates if the recurring feature is active for this template.|
|nbOccurrence|Optional|Indicates the max number of package to give to the subscriber.|
|recurringPeriodicityType|Optional|Recurring periodicity type. Possible values: 0=Daily, 1=Weekly, 2=Monthly.|
|recurringPeriodicityFrequency|Optional|Along with `recurringPeriodicityType` will determine the frequency at which the subscriber will receive its packages. For example `recurringPeriodicityType`=`0` and `recurringPeriodicityFrequency`=`2`, the subscriber is going to receive a package every 2 days.|
|reportUnitsPreviousPackage|Optional|When creating a new package for a subscriber, indicated if the remaining units of the previous packages needs to be reported (added to the new packages).|


### Request
```json
{
  "modifyPPTRecurring" : {
    "prepaidpackagetemplateid" : 123,
    "recurring" : true,
    "nbOccurrence" : 12,
    "recurringPeriodicityType" : 2,
    "recurringPeriodicityFrequency" : 12,
    "reportUnitsPreviousPackage" : true
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "modifyPrepaidPackageTemplate" : {
    "rdbDestinationZones" : {
      "destinationzoneid" : 5,
      "destinationzonename" : "Denis Destination list"
    },
    "prepaidpackagetemplateid" : 9359,
    "prepaidpackagetemplatename" : "Name",
    "resellerid" : 1,
    "priority" : 1,
    "locationzoneid" : 27,
    "destinationzoneid" : 5,
    "databyte" : 10000000,
    "mocsecond" : 60,
    "mtcsecond" : 90,
    "mosmsnumber" : 100,
    "mtsmsnumber" : 120,
    "perioddays" : 45,
    "deleted" : false,
    "esimSponsor" : 102,
    "cost" : 15.5,
    "uiVisible" : false,
    "throttlingActive" : true,
    "throttlingThreshold1Perc" : 70,
    "throttlingThreshold1Limit" : 256,
    "throttlingThreshold2Perc" : 90,
    "throttlingThreshold2Limit" : 128,
    "throttlingErrorAction" : 1,
    "recurring" : true,
    "nbOccurrence" : 12,
    "recurringPeriodicityType" : 2,
    "recurringPeriodicityFrequency" : 12,
    "reportUnitsPreviousPackage" : true,
    "resellerName" : "PDEL Reseller",
    "sponsorName" : "SP02",
    "zone" : {
      "locationZoneId" : 27,
      "locationZoneName" : "PDEL - Test eSIM",
      "countryList" : [ {
        "continent" : "Europe",
        "countryId" : 21,
        "countryName" : "Belgium",
        "countryIso2" : "be",
        "countryCode" : 32
      }, {
        "continent" : "Europe",
        "countryId" : 100,
        "countryName" : "Italy",
        "countryIso2" : "it",
        "countryCode" : 39
      } ],
      "operatorList" : [ {
        "operId" : 477,
        "operatorName" : "H3G S p A ",
        "tadigList" : [ "ITAH3" ],
        "mccMncList" : [ "222-99" ],
        "countryId" : 100
      }, {
        "operId" : 79,
        "operatorName" : "Proximus PLC",
        "tadigList" : [ "BELTB" ],
        "mccMncList" : [ "206-01" ],
        "countryId" : 21
      } ]
    },
    "useSingleCounterForCall" : true
  }
}
```
### Remark(s)

- If `recurring` is `true`, then `nbOccurrence`, `recurringPeriodicityType`, `recurringPeriodicityFrequency`, `reportUnitsPreviousPackage` are mandatory
- If `recurring` is `true`, `nbOccurrence` remains optional, but only for monthly recurring package template. If not provided, it means there won't be any stop the recurring package (infinite number of package will be given).


## 4.9 modifyPPTThrottling

### Description
This request can be used to modify the throttling configuration a prepaid package template.
Please refer to OCS User guide ( available from OCS UI) for a full description of the recurring and throttling features.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|throttlingActive|Mandatory|Indicates if the throttling feature is active for this template.|
|throttlingThreshold1Perc|Optional|First threshold for throttling, in percentage of the total volume of the package. See possible values in below remarks.|
|throttlingThreshold1Limit|Optional|Limit to apply when the subscriber is crossing the first threshold.|
|throttlingThreshold2Perc|Optional|Second threshold for throttling, in percentage of the total volume of the package. See possible values in below remarks.|
|throttlingThreshold2Limit|Optional|Limit to apply when the subscriber is crossing the second threshold.|
|throttlingErrorAction|Optional|What is happening to the package if the throttling request failed to reach the subscriber. Possible values are: 0=User can continue to use the template (no speed limitation), 1=Package is blocked and user cannot use it anymore.|


### Request
```json
{
  "modifyPPTThrottling" : {
    "prepaidpackagetemplateid" : 123,
    "throttlingActive" : true,
    "throttlingThreshold1Perc" : 70,
    "throttlingThreshold1Limit" : 256,
    "throttlingThreshold2Perc" : 90,
    "throttlingThreshold2Limit" : 128,
    "throttlingErrorAction" : 1
  }
}
```
### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "modifyPrepaidPackageTemplate" : {
    "rdbDestinationZones" : {
      "destinationzoneid" : 5,
      "destinationzonename" : "Denis Destination list"
    },
    "prepaidpackagetemplateid" : 9359,
    "prepaidpackagetemplatename" : "Name",
    "resellerid" : 1,
    "priority" : 1,
    "locationzoneid" : 27,
    "destinationzoneid" : 5,
    "databyte" : 10000000,
    "mocsecond" : 60,
    "mtcsecond" : 90,
    "mosmsnumber" : 100,
    "mtsmsnumber" : 120,
    "perioddays" : 45,
    "deleted" : false,
    "esimSponsor" : 102,
    "cost" : 15.5,
    "uiVisible" : false,
    "throttlingActive" : true,
    "throttlingThreshold1Perc" : 70,
    "throttlingThreshold1Limit" : 256,
    "throttlingThreshold2Perc" : 90,
    "throttlingThreshold2Limit" : 128,
    "throttlingErrorAction" : 1,
    "recurring" : true,
    "nbOccurrence" : 12,
    "recurringPeriodicityType" : 2,
    "recurringPeriodicityFrequency" : 12,
    "reportUnitsPreviousPackage" : true,
    "resellerName" : "PDEL Reseller",
    "sponsorName" : "SP02",
    "zone" : {
      "locationZoneId" : 27,
      "locationZoneName" : "PDEL - Test eSIM",
      "countryList" : [ {
        "continent" : "Europe",
        "countryId" : 21,
        "countryName" : "Belgium",
        "countryIso2" : "be",
        "countryCode" : 32
      }, {
        "continent" : "Europe",
        "countryId" : 100,
        "countryName" : "Italy",
        "countryIso2" : "it",
        "countryCode" : 39
      } ],
      "operatorList" : [ {
        "operId" : 477,
        "operatorName" : "H3G S p A ",
        "tadigList" : [ "ITAH3" ],
        "mccMncList" : [ "222-99" ],
        "countryId" : 100
      }, {
        "operId" : 79,
        "operatorName" : "Proximus PLC",
        "tadigList" : [ "BELTB" ],
        "mccMncList" : [ "206-01" ],
        "countryId" : 21
      } ]
    },
    "useSingleCounterForCall" : true
  }
}
```
### Remark(s)

- `throttlingThreshold1Perc` and `throttlingThreshold1Limit` are optional, but if one is set in the request, the other must be provided
- `throttlingThreshold2Perc` and `throttlingThreshold2Limit` are optional, but if one is set in the request, the other must be provided
- `throttlingErrorAction` is mandatory if `throttlingActive` is `true`
-             Possible values for `throttlingThreshold1Limit` and `throttlingThreshold2Limit` in request, those are speed limitation in Kbit:
               - 128
               - 256
               - 384
               - 512
               - 1024
               - 3072
               - 5120
               - 7680
               - 10240
               - 20480



# 5. Tariff
## 5.1 listResellerTariff

### Description
This request can be used to list the reseller (customer) tariffs (the cost for the customer). You can list them all, or just the
ones of a specific reseller.


### 5.1.1 By reseller
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
### 5.1.2 No search keys
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


## 5.2 listSubscriberTariff

### Description
This request can be used to list the subscriber tariffs. The ones used by a customer to charge
its subscribers. You can list them all, or just the ones of a specific reseller.


### 5.2.1 By reseller
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
### 5.2.2 No search keys
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


## 5.3 listTariffRule

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


## 5.4 getCustomerTariff

### Description
This request can be used to list the rules (costs) of the customer tariff. The tariff that is used
to charge the customer.

The request takes as input the reseller ID of the customer.


### Request
```json
{
  "getCustomerTariff" : 1
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
        "networkId" : 9,
        "continent" : "Europe",
        "countryCode" : 355,
        "countryName" : "Albania",
        "countryIso2" : "al",
        "utcOffset" : "+01:00",
        "operatorName" : "TELEKOM ALBANIA SH A",
        "mccMncs" : [ {
          "mcc" : "276",
          "mnc" : "01"
        } ],
        "tadigs" : [ "ALBAM" ]
      },
      "currency" : {
        "currencyid" : 1,
        "currencycode" : "EUR",
        "currencyname" : "Euro"
      },
      "sponsor" : {
        "sponsorid" : 101,
        "imsiprefix" : 24801,
        "pricingplanid" : 101,
        "sponsorname" : "Telia Estonia",
        "deleted" : false,
        "displayname" : "SP01"
      },
      "roamingplanruleid" : 9794,
      "roamingplanid" : 1,
      "networkid" : 9,
      "sponsorid" : 101,
      "sponsoridx" : 101,
      "active" : true,
      "mocallrate" : 0.429,
      "mosmsrate" : 0.033,
      "datarate" : 0.0165,
      "currencyid" : 1,
      "startdate" : "2021-12-20T00:00:00",
      "isDiscounted" : true,
      "hidden" : false,
      "dailyCap" : false
    }, {
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
      "sponsor" : {
        "sponsorid" : 1,
        "imsiprefix" : 99999,
        "pricingplanid" : 7,
        "sponsorname" : "PDEL-Spons",
        "deleted" : false,
        "displayname" : "PDEL-Spons-Display"
      },
      "roamingplanruleid" : 9790,
      "roamingplanid" : 1,
      "networkid" : 477,
      "sponsorid" : 1,
      "sponsoridx" : 1,
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

- The numeric value of `getCustomerTariff` is the id of the reseller of the customer


# 6. Statistics
## 6.1 getSubscriberActivePeriod

### Description
This request can be used the active period of a subscriber by checking the subscriber usages in DB. The request
will return the date of the first usage and the date of the last usage of the subscriber.


### 6.1.1 By subscriber ID
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
### 6.1.2 By IMSI
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
### 6.1.3 By ICCID
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
### 6.1.4 By MSISDN
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
### 6.1.5 By multi imsi
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
### 6.1.6 By Activation code
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


## 6.2 subscriberUsageOverPeriod

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


### 6.2.1 By subscriber ID
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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
          "imsi" : 24801,
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
          "imsi" : 24801,
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
          "imsi" : 24801,
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
          "imsi" : 24801,
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
          "imsi" : 24801,
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
          "imsi" : 24801,
          "sponsorImsi" : 248010416000008,
          "accountChargeEntity" : false
        } ]
      } ]
    } ]
  }
}
```
### 6.2.2 By IMSI
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.2.3 By ICCID
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.2.4 By MSISDN
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.2.5 By multi imsi
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.2.6 By Activation code
#### Request
```json
{
  "subscriberUsageOverPeriod" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


## 6.3 subscriberNetworkEventsOverPeriod

### Description
This request can be used to retrieve the network events of a subscriber over a certain period. The period
is delimited with a start date (included) and an end date (included). The period cannot exceed 1 week.


### 6.3.1 By subscriber ID
#### Request
```json
{
  "subscriberNetworkEventsOverPeriod" : {
    "subscriber" : {
      "subscriberId" : 1000
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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
### 6.3.2 By IMSI
#### Request
```json
{
  "subscriberNetworkEventsOverPeriod" : {
    "subscriber" : {
      "imsi" : "12345678901234"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.3.3 By ICCID
#### Request
```json
{
  "subscriberNetworkEventsOverPeriod" : {
    "subscriber" : {
      "iccid" : "123456789012345678"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.3.4 By MSISDN
#### Request
```json
{
  "subscriberNetworkEventsOverPeriod" : {
    "subscriber" : {
      "msisdn" : "123456789123"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.3.5 By multi imsi
#### Request
```json
{
  "subscriberNetworkEventsOverPeriod" : {
    "subscriber" : {
      "multiImsi" : "12345678901234"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### 6.3.6 By Activation code
#### Request
```json
{
  "subscriberNetworkEventsOverPeriod" : {
    "subscriber" : {
      "activationCode" : "Activation code"
    },
    "period" : {
      "start" : "2025-08-08",
      "end" : "2025-08-03"
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

- To get complete answer description, please refer to first example.


### Remark(s)

- This request is best used with the subscriber ID, if you already have it, use it.


# 7. SMS
## 7.1 sendMtSms

### Description
This request can be used to send a SMS to one of your subscribers. The SMS
will be sent via MAP MT-Forward-Sm request.

The destination of the SMS can either be the subscriber IMSI, or its MSISDN. When using the MSISDN, the MSISDN
must be the currently active MSISDN in the OCS.

The SMS to send can contain unicode characters. Unicode characters must be provided as `\\uXXXX`, where `XXXX` is a hex value. Please note that you need to send two backslashes before the u.

If there is at least one Unicode character in the text, then whole text will be converted into Unicode, and SMS length will be limited to 70 characters.

Example 1 : No unicode<br>
Original message: `Test 123 Тест`<br>
Message in JSON: `Test 123 Тест`

Example 2 : With unicode<br>
Original message: Hello 😊  <br>
Message in JSON: `Hello \\ud83d\\ude0a`


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|imsi|Optional|IMSI of the destination that will receive the SMS|
|msisdn|Optional|MSISDN of the destination that will receive the SMS|
|text|Mandatory|The text to send, with support of Unicode.|
|senderId|Mandatory|MSISDN or any text identification of the sender|


### 7.1.1 IMSI
#### Request
```json
{
  "sendMtSms" : {
    "imsi" : 123456789,
    "text" : "Msg to send",
    "senderId" : "Sender"
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
### 7.1.2 MSISDN
#### Request
```json
{
  "sendMtSms" : {
    "msisdn" : 123456789,
    "text" : "Msg to send",
    "senderId" : "Sender"
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
# 8. Network profile
## 8.1 listNetworkProfile

### Description
This request can be used to list your Network profile(s). You can provide:
- Both `resellerId` and `sponsorId`: the request will return the single Network profile for this specific reseller and sponsor.
- Only `resellerId`: the request will return the Network profile(s) of this specific reseller, for all possible sponsor(s).
- Only `sponsorId`: the request will return the Network profile(s) of this specific sponsor, for all possible reseller(s) (yours and your sub-resellers).
- None of `resellerId` and `sponsorId`: the request will return all your Network profile(s), for all possible sponsor(s), for all possible reseller(s) (yours and your sub-resellers).


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|resellerId|Optional|To restrict the search to a specific reseller. Relevant when you have sub-resellers.|
|sponsorId|Optional|To restrict the search to a specific sponsor. Relevant when you use more than one sponsor.|


### Outputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|id|Optional|Internal Id of the network profile.|
|name|Optional|The name of the network profile.|
|sponsorId|Optional|Internal Id of the sponsor.|
|sponsorName|Optional|The name of the sponsor.|
|resellerId|Optional|Internal Id of the reseller owning the network profile.|
|resellerName|Optional|The name of the reseller owning the network profile.|
|allowedListId|Optional|Internal Id of the HLR/HSS allowed list.|


### 8.1.1 Both resellerId and sponsorId
#### Request
```json
{
  "listNetworkProfile" : {
    "resellerId" : 10,
    "sponsorId" : 108
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
  "listNetworkProfile" : [ {
    "id" : 105,
    "name" : "PDEL test Modif",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 162
  } ]
}
```
### 8.1.2 Only resellerId
#### Request
```json
{
  "listNetworkProfile" : {
    "resellerId" : 10
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
  "listNetworkProfile" : [ {
    "id" : 46,
    "name" : "New list PDEL test 2",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 134
  }, {
    "id" : 105,
    "name" : "PDEL test Modif",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 162
  } ]
}
```
### 8.1.3 Only sponsorId
#### Request
```json
{
  "listNetworkProfile" : {
    "sponsorId" : 108
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
  "listNetworkProfile" : [ {
    "id" : 46,
    "name" : "New list PDEL test 2",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 134
  }, {
    "id" : 105,
    "name" : "PDEL test Modif",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 162
  } ]
}
```
### 8.1.4 None of resellerId and sponsorId
#### Request
```json
{
  "listNetworkProfile" : { }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listNetworkProfile" : [ {
    "id" : 46,
    "name" : "New list PDEL test 2",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 134
  }, {
    "id" : 105,
    "name" : "PDEL test Modif",
    "sponsorId" : 108,
    "sponsorName" : "SP05 (ID=108)",
    "resellerId" : 10,
    "resellerName" : "PDEL Reseller 3",
    "allowedListId" : 162
  } ]
}
```
## 8.2 createLocationZone

### Description
This request can be used to create a new Location zone. The backend will perform the following tests before creating the new Location zone:
- Does the `locationZoneName` already exist in the DB (for the reseller of the `networkProfileId`).
- Does ALL the TADIG in `tadigList` exist in the DB. In case one (or more) TADIG doesn't not exist in the DB, a dedicated error with code `10001` will be returned. The answer will also contain the list of unknown TADIG.
- Is there already a Location zone in the DB with the exact same operators. Via the API, you cannot create a new Location zone with the same operator set of another Location zone. If another Location zone with same operator set already exist, the backend will return a dedicated error with code `10002`. The answer will contain the name and the ID of the existing Location zone. So you can reuse the existing Location zone to create a new package template, instead of duplicating the Location zone. This will prevent to create multiple identical Location zones.
- All operator(s) provided in the request for the new location zone must be available/allowed. If you use the UI to create the LZ, the UI will propose you only the available/allowed operators. To be available/allowed, an operator needs to satisfy the following conditions:
   - The operator must be present in your reseller tariff. If it's not the case, the subscribers won't be able to use their prepaid packages.
   - The operator must be provided by the sponsor. If it's not the case, the subscribers won't be able to use their prepaid packages.
   - The operator cannot be (too) expensive. We have configured a limit for the data cost. Above this limit, the operator is considered to be too expensive to be used in a location zone.


### Inputs
|Parameter|Presence|Description|
|---------|--------|-----------|
|networkProfileId|Mandatory|Network profile that will own the new Location zone.|
|locationZoneName|Mandatory|The name for the new Location zone.|
|tadigList|Mandatory|List of TADIG of the operators to add in the new Location zone.|


### 8.2.1 Success
#### Request
```json
{
  "createLocationZone" : {
    "networkProfileId" : 79,
    "locationZoneName" : "New LZ name",
    "tadigList" : [ "AZER1", "QWER1" ]
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
  "createLocationZone" : {
    "newLZ" : {
      "Id" : 1924,
      "name" : "new LZ 2"
    }
  }
}
```
### 8.2.2 LZ name already exist
#### Request
```json
{
  "createLocationZone" : {
    "networkProfileId" : 79,
    "locationZoneName" : "New LZ name",
    "tadigList" : [ "AZER1", "QWER1" ]
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 4,
    "msg" : "A location zone already exist with this name (for this reseller)"
  }
}
```
### 8.2.3 Unknown operator
#### Request
```json
{
  "createLocationZone" : {
    "networkProfileId" : 79,
    "locationZoneName" : "New LZ name",
    "tadigList" : [ "AZER1", "QWER1" ]
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 10001,
    "msg" : "Unknown TADIG, see list in this answer"
  },
  "createLocationZone" : {
    "invalidTadigs" : [ "AZER1", "QWER1" ]
  }
}
```
### 8.2.4 LZ with same operator(s) already exist
#### Request
```json
{
  "createLocationZone" : {
    "networkProfileId" : 79,
    "locationZoneName" : "New LZ name",
    "tadigList" : [ "AZER1", "QWER1" ]
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 10002,
    "msg" : "LZ with same operator already exist"
  },
  "createLocationZone" : {
    "existingLZ" : {
      "Id" : 1923,
      "name" : "Name of the LZ with the same operator(s)"
    }
  }
}
```
### 8.2.5 Operator(s) not in reseller tariff
#### Request
```json
{
  "createLocationZone" : {
    "networkProfileId" : 79,
    "locationZoneName" : "New LZ name",
    "tadigList" : [ "AZER1", "QWER1" ]
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 10003,
    "msg" : "Some operator(s) not allowed in reseller tariff"
  },
  "createLocationZone" : {
    "invalidTadigs" : [ "JPNKD" ]
  }
}
```
### 8.2.6 Operator(s) not provided by sponsor, or too expensive
#### Request
```json
{
  "createLocationZone" : {
    "networkProfileId" : 79,
    "locationZoneName" : "New LZ name",
    "tadigList" : [ "AZER1", "QWER1" ]
  }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 10004,
    "msg" : "Some operator(s) are not available for this operation."
  },
  "createLocationZone" : {
    "invalidTadigs" : [ "BGR01", "DNKIA" ]
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
| 14 | OPERATION_IMPOSSIBLE |
| 15 | HLR_API_ERROR |
| 16 | STEERING_API_ERROR |
| 17 | SUBS_END_OF_LIFE |
| 100 | TRAFFIC_CONTROL_LIMIT_EXCEEDED |

