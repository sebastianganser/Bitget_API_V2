---
conversion_date: "2025-03-12"
document_title: "Get Discount Rate | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Discount-Rate"
---

# Get Discount Rate | Bitget API

**Frequency limit:** 5 times/1s (IP)

## Description
Get Discount Rate

## HTTP Request
```
GET /api/v2/mix/market/discount-rate
```

## Request Parameters
N/A

## Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/discount-rate"
```

## Response Parameters
| Parameter         | Type   | Description              |
|------------------|--------|--------------------------|
| coin              | String | Assets                   |
| userLimit         | String | Individual limit         |
| totalLimit        | String | Total platform limit     |
| discountRateList  | List   | Tier discount rate       |
| └ tier            | String | Tier                     |
| └ minAmount       | String | Min                      |
| └ maxAmount       | String | Max                      |
| └ discountRate    | String | Discount rate            |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1725848381845,
    "data": [
        {
            "coin": "BTC",
            "userLimit": "100",
            "totalLimit": "1500",
            "discountRateList": [
                {
                    "tier": "1",
                    "minAmount": "0",
                    "maxAmount": "10000",
                    "discountRate": "0.99"
                },
                {
                    "tier": "2",
                    "minAmount": "10000",
                    "maxAmount": "100000",
                    "discountRate": "0.95"
                },
                {
                    "tier": "3",
                    "minAmount": "100000",
                    "maxAmount": "200000",
                    "discountRate": "0.9"
                },
                {
                    "tier": "4",
                    "minAmount": "200000",
                    "maxAmount": "-1",
                    "discountRate": "0.8"
                }
            ]
        },
        {
            "coin": "ETH",
            "userLimit": "50000",
            "totalLimit": "500000000",
            "discountRateList": [
                {
                    "tier": "1",
                    "minAmount": "0",
                    "maxAmount": "100",
                    "discountRate": "0.9"
                },
                {
                    "tier": "2",
                    "minAmount": "100",
                    "maxAmount": "5000",
                    "discountRate": "0.7"
                },
                {
                    "tier": "3",
                    "minAmount": "5000",
                    "maxAmount": "-1",
                    "discountRate": "0.5"
                }
            ]
        }
    ]
}
```

