---
conversion_date: "2025-03-12"
document_title: "Get Virtual Subaccounts | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Get-Virtual-Subaccount-List"
---

# Get Virtual Subaccounts

**Frequency limit**: 10 times/1s (User ID)

## Description
Get a list of virtual sub-account

## HTTP Request
```
GET /api/v2/user/virtual-subaccount-list
```

## Request Parameters
| Parameter     | Type   | Required | Description                           |
|---------------|--------|----------|---------------------------------------|
| limit         | String | No       | Entries per page. Default: 100, maximum: 500 |
| idLessThan    | String | No       | Final sub-account ID, required for paging. |
| status        | String | No       | Sub-account status <br> - normal: Normal <br> - freeze: Freeze |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/user/virtual-subaccount-list?limit=20" \
  -H "ACCESS-KEY:*******" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:en-US" \
  -H "Content-Type: application/json"
```

## Response Parameters
| Parameter        | Type   | Description                           |
|------------------|--------|---------------------------------------|
| subAccountList   | Array  | Sub-account array                    |
| > subAccountUid  | String | Sub-account uid                      |
| > subAccountName | String | Sub-account username                 |
| > label          | String | Sub-account ApiKey note, max length 20 |
| > status         | String | Sub-account status <br> - normal: Normal <br> - freeze: Freeze <br> - del: Deleted |
| > permList       | List   | Sub-account permissions <br> - spot_trade: Spot trade <br> - contract_trade: Futures trade read-write <br> - read: Read permissions |
| > cTime          | String | Sub-account creation time            |
| > uTime          | String | Sub-account update time              |
| endId            | String | This is used when idLessThan/idGreaterThan is set as a range. |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": {
        "endId": 51,
        "subAccountList": [
            {
                "subAccountUid": "********",
                "subAccountName": "****@*****.com",
                "status": "normal",
                "permList": [
                    "read",
                    "spot_trade",
                    "contract_trade"
                ],
                "label": "mySub01",
                "accountType":"hosting",
                "bindingTime":"1653287983475",
                "cTime": "1653287983475",
                "uTime": "1682660169573"
            }
        ]
    }
}
```

