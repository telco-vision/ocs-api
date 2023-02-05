## [1 Reseller](#11-listreselleraccount)

[1.1 listResellerAccount](#11-listreselleraccount)

## [2 Subscriber](#21-listsubscriber)

[2.1 listSubscriber](#21-listsubscriber)

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
      "name" : "PDEL Reseller",
      "account" : [ {
        "id" : 4,
        "name" : "PDEL - Second account",
        "balance" : 660.5500000000001
      }, {
        "id" : 7,
        "name" : "PDEL - Subs X",
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
      "name" : "PDEL Reseller 3",
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
      "name" : "PDEL Reseller 3",
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
      "account" : "PDEL - Second account",
      "reseller" : "PDEL Reseller"
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
      "account" : "PDEL - Second account",
      "reseller" : "PDEL Reseller"
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
      "account" : "PDEL - Second account",
      "reseller" : "PDEL Reseller"
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
      "account" : "PDEL - Second account",
      "reseller" : "PDEL Reseller"
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
      "account" : "PDEL - Second account",
      "reseller" : "PDEL Reseller"
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
      "account" : "PDEL - Second account",
      "reseller" : "PDEL Reseller"
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
      "reseller" : "PDEL Reseller 3",
      "lastMcc" : 334,
      "lastMnc" : 50
    } ],
    "hasMore" : false,
    "nbFound" : 1
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

