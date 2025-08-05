---
conversion_date: "2025-03-12"
document_title: "Get Leveraged long-short ratio Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Margin-Ls-Ratio"
---

# Get Leveraged long-short ratio Data | Bitget API

**Frequency limit:** 1 times/1s (IP)

## Description
The long-short position ratio for a specific coin in cross and isolated margin accounts.

## HTTP Request
```
GET /api/v2/margin/market/long-short-ratio
```

## Request Parameters
| Parameter | Type   | Required | Description                                      |
|-----------|--------|----------|--------------------------------------------------|
| symbol    | String | Yes      | Trading pair                                     |
| period    | String | No       | Default: 24h, support: `24h`, `30d`              |
| coin      | String | No       | Base coin or quote coin, default: base coin     |

## Request Example
```
curl "https://api.bitget.com/api/v2/margin/market/long-short-ratio?symbol=BTCUSDT"
```

## Response Parameters
| Parameter       | Type   | Description         |
|----------------|--------|---------------------|
| longShortRatio | String | long short ratio    |
| ts             | String | Milliseconds time   |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": [
        {
            "ts": "1713942000000",
            "longShortRatio": "-0.96"
        },
        {
            "ts": "1713942000000",
            "longShortRatio": "-0.96"
        }
    ]
}
```

