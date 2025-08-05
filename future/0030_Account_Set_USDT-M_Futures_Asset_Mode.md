---
conversion_date: "2025-03-19"
document_title: "Set USDT-M Futures Asset Mode | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Set-Asset-Mode"
---

# Set USDT-M Futures Asset Mode | Bitget API

## Set USDT-M Futures Asset Mode

**Frequency limit:** 2 times/1s (uid)

### Description
Set USDT-M Futures Asset Mode

### HTTP Request
```
POST /api/v2/mix/account/set-asset-mode
```

### Request Parameters
| Parameter    | Type   | Required | Description                             |
|--------------|--------|----------|-----------------------------------------|
| productType  | String | Yes      | Product type                            |
|              |        |          | USDT-FUTURES: USDT professional futures |
|              |        |          | SUSDT-FUTURES: USDT professional futures demo |
| assetMode    | String | Yes      | Asset mode                              |
|              |        |          | single: Single asset mode               |
|              |        |          | union: Multi-assets mode                |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/account/set-asset-mode" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"productType": "USDT-FUTURES","assetMode": "union"}'
```

### Response Parameters
| Parameter | Type   | Description                               |
|-----------|--------|-------------------------------------------|
| data      | String | 'success' means setting the asset mode was successful |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1725848356656,
    "data": "success"
}
```
