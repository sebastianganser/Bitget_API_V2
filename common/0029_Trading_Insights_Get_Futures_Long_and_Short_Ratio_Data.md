---
conversion_date: "2025-03-12"
document_title: "Get Futures Long and Short Ratio Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Long-Short"
---

# Get Futures Long and Short Ratio Data | Bitget API

## Get Futures Long and Short Ratio Data

**Rate limit:** 1 req/1s (IP)

### Description

Get Futures Long and Short Ratio Data

### HTTP Request

```
GET /api/v2/mix/market/long-short
```

### Request Parameters

| Parameter | Type   | Required | Description                       |
|----------|--------|----------|-----------------------------------|
| symbol   | String | Yes      | Trading pair                      |
| period   | String | No       | - default: 5m, support: <br>5m <br>15m <br>30m <br>1h <br>2h <br>4h <br>6h <br>12h <br>1Dutc |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/market/long-short?symbol=BTCUSDT"
```

### Response Parameters

| Parameter       | Type   | Description         |
|----------------|--------|---------------------|
| longRatio       | String | Long Ratio          |
| shortRatio      | String | Short Ratio         |
| longShortRatio  | String | Long Short Ratio    |
| ts              | String | Milliseconds time   |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "longRatio": "0.01",
            "shortRatio": "0.12",
            "longShortRatio": "1.2",
            "ts": "1714020600000"
        },
        {
            "longRatio": "0.01",
            "shortRatio": "0.12",
            "longShortRatio": "1.2",
            "ts": "1714020600000"
        }
    ]
}
```

