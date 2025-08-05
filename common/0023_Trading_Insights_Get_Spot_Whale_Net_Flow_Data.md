---
conversion_date: "2025-03-12"
document_title: "Get Spot Whale Net Flow Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Whale-Net-Flow"
---

# Get Spot Whale Net Flow Data | Bitget API

## Get Spot Whale Net Flow Data
**Rate limit:** 1 req/s (IP)

### Description
Get spot fund flow

### HTTP Request
```
GET /api/v2/spot/market/whale-net-flow
```

### Request Parameters
| Parameter | Type   | Required | Description     |
|-----------|--------|----------|-----------------|
| symbol    | String | Yes      | Trading pair    |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/spot/market/fund-flow?symbol=BTCUSDT"
```

### Response Parameters
| Parameter | Type   | Description               |
|-----------|--------|---------------------------|
| volume    | String | Whale buy sell volume     |
| date      | String | Milliseconds time         |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "volume": "-1.1",
            "date": "1713942000000"
        },
        {
            "volume": "-1.1",
            "date": "1713942000000"
        },
        {
            "volume": "-1.1",
            "date": "1713942000000"
        },
        {
            "volume": "-1.1",
            "date": "1713942000000"
        },
        {
            "volume": "-1.1",
            "date": "1713942000000"
        }
    ]
}
```

