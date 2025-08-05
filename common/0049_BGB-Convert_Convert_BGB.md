---
conversion_date: "2025-03-12"
document_title: "Convert BGB | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/bgb-convert/"
---

# Convert BGB | Bitget API

## Convert BGB

**Frequency limit:** 10 times/1s (User ID)

### Description
Convert BGB

### HTTP Request
```
POST /api/v2/convert/bgb-convert
```

### Request Parameters
| Parameter | Type   | Required | Description |
|-----------|--------|----------|-------------|
| coinList  | String | Yes      | swap coins  |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/convert/bgb-convert" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
  -d '{"coinList": ["EOS","GROK"]}'
```

### Response Parameters
| Parameter  | Type   | Description    |
|------------|--------|----------------|
| orderList  | String |                |
| > coin     | String | Coin swap      |
| > orderId  | String | swap order Id  |

### Response Example
```json
{
  "code": "00000",
  "data": {
    "orderList": [
      {
        "coin": "EOS",
        "orderId": "1233431213"
      },
      {
        "coin": "GROK",
        "orderId": "1233431213"
      }   
    ]
  },
  "msg": "success",
  "requestTime": 1627293612502
}
```
