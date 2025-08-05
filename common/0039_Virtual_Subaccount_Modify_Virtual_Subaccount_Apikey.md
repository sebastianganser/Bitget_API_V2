---
conversion_date: "2025-03-12"
document_title: "Modify Virtual Subaccount Apikey | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Modify-Virtual-Subaccount-ApiKey"
---

# Modify Virtual Subaccount Apikey | Bitget API

## Modify Virtual Subaccount Apikey

**Frequency limit:** 5 times/1s (User ID)

### Description
Modify the virtual sub-account apikey

### HTTP Request
```
POST /api/v2/user/modify-virtual-subaccount-apikey
```

### Request Parameters
| Parameter         | Type           | Required | Description                                                |
|------------------|----------------|----------|------------------------------------------------------------|
| subAccountUid     | String         | Yes      | Sub-account uid                                            |
| passphrase        | String         | Yes      | Passcode English letters of 8−32 characters + numbers      |
| label             | String         | Yes      | Note Length 20                                             |
| ipList            | List<String>   | No       | ip whitelist<br>Up to 30, if not then ip whitelist is set to empty. |
| permList          | List<String>   | No       | Sub-account permissions<br>spot_trade: Spot trade<br>margin_trade: Spot Margin trade<br>contract_trade: Futures trade read-write<br>read: Read permissions |
| subAccountApiKey  | String         | Yes      | Sub-account ApiKey                                         |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/user/modify-virtual-subaccount-apikey" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \  
   -d '{
     "subAccountUid":"1",
     "subAccountApiKey":"xx_xxx", 
     "passphrase":"xxx",
     "permList":["spot_trade","contract_trade"],
     "label":"label",
     "ipList":["127.0.0.1","127.0.0.2"]
   }'
```

### Response Parameters
| Parameter         | Type         | Description                                      |
|------------------|--------------|--------------------------------------------------|
| subAccountUid     | String       | Sub-account uid                                  |
| subAccountApiKey  | String       | Sub-account apikey                               |
| secretKey         | String       | secretKey                                        |
| permList          | List         | Sub-account permissions<br>spot_trade: Spot trade<br>margin_trade: Spot Margin trade<br>contract_trade: Futures trade read-write<br>read: Read permissions |
| label             | String       | Sub-account apikey note                          |
| ipList            | List         | Sub-account apikey ip whitelist                  |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1682660169412,
    "data": {
        "subAccountUid": "1",
        "label": "sub api",
        "subAccountApiKey": "xx_xxx",
        "secretKey": "xxx",
        "permList": [
            "spot_trade",
            "contract_trade"
        ],
        "ipList": [
            "127.0.0.1"
        ]
    }
}
```

