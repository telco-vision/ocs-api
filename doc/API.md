## [1 Reseller](#11-listcustomeraccount)

[1.1 listCustomerAccount](#11-listcustomeraccount)

## [Error codes](#error-codes)

# 1. Reseller
## 1.1 listCustomerAccount

### Description
This request can be used to retrieve the list of accounts. You can retrieve the list of a specific reseller
or all accounts of all your reseller.


### 1.1.1 Account of all resellers
#### Request
```json
{
  "listCustomerAccount" : { }
}
```
#### Answer

```json
{
  "status" : {
    "code" : 0,
    "msg" : "OK"
  },
  "listCustomerAccount" : {
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
### 1.1.2 UAccount of specific reseller
#### Request
```json
{
  "listCustomerAccount" : {
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
  "listCustomerAccount" : {
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

