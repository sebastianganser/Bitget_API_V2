---
conversion_date: "2025-03-12"
document_title: "Get Futures Active Long Short Position Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Position-Long-Short"
---

# Get Futures Active Long Short Position Data | Bitget API

**Rate limit:** 1 req/s (IP)

## Description

Get Futures Active Long Short Position Data.

## HTTP Request

```
GET /api/v2/mix/market/position-long-short
```

## Request Parameters

| Parameter | Type   | Required | Description                                                                 |
|----------|--------|----------|-----------------------------------------------------------------------------|
| symbol   | String | Yes      | Trading pair                                                               |
| period   | String | No       | - default: 5m, support: 5m, 15m, 30m, 1h, 2h, 4h, 6h, 12h, 1d |

## Request Example

```
curl "https://api.bitget.com/api/v2/mix/market/position-long-short?symbol=BTCUSDT"
```

## Response Parameters

| Parameter              | Type   | Description              |
|------------------------|--------|--------------------------|
| longPositionRatio      | String | Long Position Ratio      |
| shortPositionRatio     | String | Short Position Ratio     |
| longShortPositionRatio | String | Long Short Position Ratio|
| ts                     | String | Milliseconds time        |

## Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "longPositionRatio": "0.01",
            "shortPositionRatio": "0.12",
            "longShortPositionRatio": "1.2",
            "ts": "1714020600000"
        },
        {
            "longPositionRatio": "0.01",
            "shortPositionRatio": "0.12",
            "longShortPositionRatio": "1.2",
            "ts": "1714020600000"
        }
    ]
}
```

