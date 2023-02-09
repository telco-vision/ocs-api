## [1 Reseller](#11-listreselleraccount)

[1.1 listResellerAccount](#11-listreselleraccount)

## [2 Subscriber](#21-listsubscriber)

[2.1 listSubscriber](#21-listsubscriber)

## [3 Prepaid package](#31-listprepaidpackagetemplate)

[3.1 listPrepaidPackageTemplate](#31-listprepaidpackagetemplate)

## [4 Tariff](#41-listresellertariff)

[4.1 listResellerTariff](#41-listresellertariff)

[4.2 listSubscriberTariff](#42-listsubscribertariff)

[4.3 listTariffRule](#43-listtariffrule)

## [Error codes](#error-codes)

# 1. Reseller
## 1.1 listResellerAccount

### Description
This request can be used to retrieve the list of accounts. You can retrieve the list of a specific reseller
or all accounts of all your reseller.


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
- Account prefix
- eSIM activation code


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
#### Remark(s)

- `imsiPrefix` the prefix must be minimum 10 digits


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
#### Remark(s)

- `iccidPrefix` the prefix must be minimum 13 digits


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
  "listSubscriberTariff" : {
    "resellerId" : 1
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

