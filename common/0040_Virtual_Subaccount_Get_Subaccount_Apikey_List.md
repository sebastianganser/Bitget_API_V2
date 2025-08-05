---
conversion_date: "2025-03-12"
document_title: "Get Subaccount Apikey List | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Get-Virtual-Subaccount-ApiKey-List"
---

# Get Subaccount Apikey List | Bitget API

## Get Subaccount Apikey List

**Rate Limit**: 5 req/sec/UID

### Description

Get sub-account api list

### HTTP Request

```
GET /api/v2/user/virtual-subaccount-apikey-list
```

### Request Parameters

| Parameter      | Type   | Required | Description           |
|----------------|--------|----------|-----------------------|
| subAccountUid  | String | Yes      | Sub-account uid       |

### Request Example

```bash
curl -X GET "https://api.bitget.com/api/v2/user/virtual-subaccount-apikey-list?subAccountUid=1" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameters

| Parameter          | Type   | Description                  |
|-------------------|--------|------------------------------|
| subAccountUid      | String | Sub-account uid              |
| subAccountApiKey   | String | Sub-account ApiKey           |
| permList           | List   | Sub-account permissions      |

#### Permissions include:
- `spot_trade`: Spot trade  
- `margin_trade`: Spot Margin trade  
- `contract_trade`: Futures trade read-write  
- `read`: Read permissions

| Parameter | Type | Description               |
|----------|------|---------------------------|
| label    | String | Sub-account apikey note |
| ipList   | List   | IP whitelist             |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1682661432874,
    "data": [
        {
            "subAccountUid": "1",
            "label": "1682396356594",
            "subAccountApiKey": "xx_xxx",
            "permList": [
                "spot_trade",
                "margin_trade",
                "contract_trade"
            ],
            "ipList": [
                "127.0.0.1"
            ]
        }
    ]
}
```

