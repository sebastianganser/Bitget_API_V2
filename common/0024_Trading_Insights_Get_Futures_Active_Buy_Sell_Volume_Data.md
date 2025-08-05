---
conversion_date: "2025-03-12"
document_title: "Get Futures Active Buy Sell Volume Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Taker-Buy-Sell"
---

# Get Futures Active Buy Sell Volume Data | Bitget API

## Get Futures Active Buy Sell Volume Data

**Rate limit:** 1 req/s (IP)

### Description

Get Futures Active Buy Sell Volume Data

### HTTP Request

```
GET /api/v2/mix/market/taker-buy-sell
```

### Request Parameters

| Parameter | Type   | Required | Description                            |
|----------|--------|----------|----------------------------------------|
| symbol   | String | Yes      | Trading pair                           |
| period   | String | No       | default: 5m, support: <br>5m<br>15m<br>30m<br>1h<br>2h<br>4h<br>6h<br>12h<br>1d |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/market/taker-buy-sell?symbol=BTCUSDT"
```

### Response Parameters

| Parameter   | Type   | Description         |
|------------|--------|---------------------|
| sellVolume | String | Sell Volume         |
| buyVolume  | String | Buy Volume          |
| ts         | String | Milliseconds time   |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "buyVolume": "0.01",
            "sellVolume": "0.12",
            "ts": "1714020600000"
        },
        {
            "buyVolume": "0.01",
            "sellVolume": "0.12",
            "ts": "1714020600000"
        }
    ]
}
```

