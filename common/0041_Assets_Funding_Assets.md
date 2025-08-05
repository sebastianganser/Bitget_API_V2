---
conversion_date: "2025-03-12"
document_title: "Funding Assets | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/account/Funding-Assets"
---

# Funding Assets | Bitget API

## Funding Assets

**Frequency limit:** 10 times/1s (User ID)

### HTTP Request
```
GET /api/v2/account/funding-assets
```

### Request Parameters
| Parameter | Type   | Required | Description         |
|-----------|--------|----------|---------------------|
| coin      | String | No       | default all coin    |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/account/funding-assets" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*******" \
  -H "ACCESS-PASSPHRASE:*****" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:en-US" \
  -H "Content-Type: application/json"
```

### Response parameters
| Parameter  | Type   | Description   |
|-----------|--------|----------------|
| data      | List<Object> | assets List |
| > coin     | String | coin          |
| > available | String | available     |
| > frozen   | String | frozen        |
| > usdtValue | String | USDT value   |

### Response Example
```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1712129301188,
  "data": [
    {
      "coin": "USDT",
      "available": "326",
      "frozen": "",
      "usdtValue": "326"
    }
  ]
}
```

