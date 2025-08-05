---
conversion_date: "2025-03-12"
document_title: "Get Futures Active Long Short Account Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Account-Long-Short"
---

# Get Futures Active Long Short Account Data | Bitget API

## Get Futures Active Long Short Account Data

**Rate limit:** 1 req/s (IP)

### Description
Get Futures Active Long Short Account Data

### HTTP Request
```
GET /api/v2/mix/market/account-long-short
```

### Request Parameters

| Parameter | Type   | Required | Description        |
|----------|--------|----------|--------------------|
| symbol   | String | Yes      | Trading pair       |
| period   | String | No       | - default: 5m, support: <br>5m<br>15m<br>30m<br>1h<br>2h<br>4h<br>6h<br>12h<br>1d |

### Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/account-long-short?symbol=BTCUSDT"
```

### Response Parameters

| Parameter            | Type   | Description              |
|---------------------|--------|--------------------------|
| longAccountRatio     | String | Long Account Ratio       |
| shortAccountRatio    | String | Short Account Ratio      |
| longShortAccountRatio| String | Long Short Account Ratio |
| ts                   | String | Millseconds time         |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "longAccountRatio": "0.01",
            "shortAccountRatio": "0.12",
            "longShortAccountRatio": "1.2",
            "ts": "1714020600000"
        },
        {
            "longAccountRatio": "0.01",
            "shortAccountRatio": "0.12",
            "longShortAccountRatio": "1.2",
            "ts": "1714020600000"
        }
    ]
}
```
