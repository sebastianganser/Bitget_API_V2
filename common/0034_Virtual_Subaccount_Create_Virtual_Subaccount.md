---
conversion_date: "2025-03-12"
document_title: "Create Virtual Subaccount | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Create-Virtual-Subaccount"
---

# Create Virtual Subaccount | Bitget API

## Create Virtual Subaccount

**Frequency limit:** 5 times/1s (User ID)

### Description
This interface currently supports the creation of virtual sub-accounts in batch. (It's required API key binding IP address)

### HTTP Request
```
POST /api/v2/user/create-virtual-subaccount
```

### Request Parameters
| Parameter       | Type         | Required | Description                                              |
|----------------|--------------|----------|----------------------------------------------------------|
| subAccountList | List<String> | Yes      | Virtual alias 8-character English letters, Global unique |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/user/create-virtual-subaccount" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"subAccountList": ["testtest"]}'
```

### Response Parameters
| Parameter        | Type   | Description                                                      |
|------------------|--------|------------------------------------------------------------------|
| failureList       | Array  | Sub-account array creation failed                                |
| - subaAccountName | String | Sub-account name                                                 |
| successList       | Array  | Sub-account array created successfully                           |
| - subaAccountUid  | String | Sub-account uid                                                  |
| - subaAccountName | String | Sub-account name                                                 |
| - status          | String | Sub-account status: normal, freeze, del                          |
| - permList        | List   | Sub-account permissions: spot_trade, contract_trade, read        |
| - label           | String | Note                                                             |
| - cTime           | String | Sub-account creation time, Unix millisecond timestamps          |
| - uTime           | String | Sub-account update time, Unix millisecond timestamps            |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1682660169412,
    "data": {
        "failureList": [
            {
                "subaAccountName": "****@*****.com"
            }
        ],
        "successList": [
            {
                "subaAccountUid": "**********",
                "subaAccountName": "****@*****.com",
                "status": "normal",
                "label": "",
                "permList": [
                    "contract_trade",
                    "spot_trade"
                ],
                "cTime": "1682660169573",
                "uTime": "1682660169573"
            }
        ]
    }
}
```

