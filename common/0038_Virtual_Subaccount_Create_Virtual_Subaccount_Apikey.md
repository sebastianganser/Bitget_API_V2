---
conversion_date: "2025-03-12"
document_title: "Create Virtual Subaccount Apikey | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Create-Virtual-Subaccount-ApiKey"
---

# Create Virtual Subaccount Apikey | Bitget API

## Create Virtual Subaccount Apikey

**Frequency limit:** 5 times/1s (User ID)

### Description
Create the virtual sub-account apikey.

### HTTP Request
```
POST /api/v2/user/create-virtual-subaccount-apikey
```

### Request Parameters
| Parameter       | Type           | Required | Description                                                                 |
|----------------|----------------|----------|-----------------------------------------------------------------------------|
| subAccountUid  | String         | Yes      | Sub-account uid                                                            |
| passphrase     | String         | Yes      | Passcode English letters of 8−32 characters + numbers                      |
| label          | String         | Yes      | Note Length 20                                                             |
| ipList         | List<String>   | No       | ip whitelist. Up to 30, if not then ip whitelist is set to empty.         |
| permList       | List           | No       | Sub-account permissions:  
- spot_trade: Spot trade  
- margin_trade: Spot Margin trade  
- contract_trade: Futures trade read-write  
- read: Read permissions |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/user/create-virtual-subaccount-apikey" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \  
   -d '{
    "subAccountUid":"1",
    "passphrase":"pssword1",
    "label":"test1_account",
    "ipList":["127.0.0.1"],
    "permList":[
        "spot_trade"
    ]
}'
```

### Response Parameters
| Parameter         | Type    | Description                                     |
|------------------|---------|-------------------------------------------------|
| subAccountUid     | String  | Sub-account uid                                 |
| subAccountApiKey  | String  | Sub-account apikey                              |
| secretKey         | String  | Sub-account private key                         |
| permList          | List    | Sub-account permissions:  
- spot_trade: Spot trade  
- margin_trade: Spot Margin trade  
- contract_trade: Futures trade read-write  
- read: Read permissions |
| label             | String  | Sub-account apikey note                         |
| ipList            | List    | ip whitelist                                    |

### Response Example
```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1682660169412,
  "data": {
    "subAccountUid": "1",
    "label": "test1_account",
    "subAccountApiKey": "xx_xxx",
    "secretKey": "xxx",
    "permList": [
      "spot_trade"
    ],
    "ipList": [
      "127.0.0.1"
    ]
  }
}
```