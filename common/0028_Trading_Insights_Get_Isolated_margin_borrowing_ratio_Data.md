---
conversion_date: "2025-03-12"
document_title: "Get Isolated margin borrowing ratio Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Margin-Iso-Borrow-Ratio"
---

# Get Isolated margin borrowing ratio Data | Bitget API

## Get Isolated margin borrowing ratio Data

**Frequency limit:** 1 times/1s (IP)

### Description

The ratio of borrowed amount in the base currency (left) and borrowed amount in the quote currency (right) in isolated margin accounts, converted to USDT.

### HTTP Request

```
GET /api/v2/mix/market/isolated-borrow-rate
```

### Request Parameters

| Parameter | Type   | Required | Description                                                                 |
|----------|--------|----------|-----------------------------------------------------------------------------|
| symbol   | String | Yes      | Trading pair                                                                |
| period   | String | No       | Default: 24h, support: <br>- 24h <br>- 30d                                   |

### Request Example

```
curl "https://api.bitget.com/api/v2/mix/market/isolated-borrow-rate?symbol=BTCUSDT"
```

### Response Parameters

| Parameter   | Type   | Description        |
|-------------|--------|--------------------|
| borrowRate  | String | borrow ratio       |
| ts          | String | Millseconds time   |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "ts": "1713942000000",
            "borrowRate": "-0.96"
        },
        {
            "ts": "1713942000000",
            "borrowRate": "-0.96"
        }
    ]
}
```

