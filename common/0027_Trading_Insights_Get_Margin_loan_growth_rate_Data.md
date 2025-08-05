
---
conversion_date: "2025-03-12"
document_title: "Get Margin loan growth rate Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Margin-Loan-Growth"
---

# Get Margin loan growth rate Data | Bitget API

## Get Margin loan growth rate Data

**Frequency limit:** 1 times/1s (IP)

### Description

The growth rate of borrowed funds for a specific coin in cross and isolated margin accounts.

### HTTP Request

```
GET /api/v2/mix/market/loan-growth
```

### Request Parameters

| Parameter | Type   | Required | Description                                              |
|----------|--------|----------|----------------------------------------------------------|
| symbol   | String | Yes      | Trading pair                                             |
| period   | String | No       | Default: 24h, support: <br>- 24h <br>- 30d                |
| coin     | String | No       | Base coin or quote coin, default: base coin              |

### Request Example

```
curl "https://api.bitget.com/api/v2/mix/market/loan-growth?symbol=BTCUSDT"
```

### Response Parameters

| Parameter   | Type   | Description        |
|------------|--------|--------------------|
| growthRate | String | growth ratio       |
| ts         | String | Milliseconds time  |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "ts": "1713942000000",
            "growthRate": "-0.96"
        },
        {
            "ts": "1713942000000",
            "growthRate": "-0.96"
        }
    ]
}
```

