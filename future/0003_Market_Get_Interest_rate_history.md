---
conversion_date: "2025-03-12"
document_title: "Get Interest rate history | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Interest-Rate"
---

# Get Interest rate history | Bitget API

## Get Interest rate history

**Frequency limit:** 5 times/1s (IP)

### Description

Get Interest rate history

### HTTP Request

```
GET /api/v2/mix/market/union-interest-rate-history
```

### Request Parameters

| Parameter | Type   | Required | Description  |
|----------|--------|----------|--------------|
| coin     | String | Yes      | Coin asset   |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/market/union-interest-rate-history?coin=USDT"
```

### Response Parameters

| Parameter              | Type  | Description              |
|------------------------|-------|--------------------------|
| coin                   | String | Assets                   |
| historyInterestRateList | List  | History Interest list     |
| > annualInterestRate   | String | Annual interest rate     |
| > dailyInterestRate    | String | Daily interest rate      |
| > ts                   | String | Interest time            |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1725948522731,
    "data": {
        "coin": "USDT",
        "historyInterestRateList": [
            {
                "ts": "1723533015946",
                "annualInterestRate": "0.02555",
                "dailyInterestRate": "0.00007"
            },
            {
                "ts": "1723446615946",
                "annualInterestRate": "0.02555",
                "dailyInterestRate": "0.00007"
            },
            {
                "ts": "1723360215946",
                "annualInterestRate": "0.02555",
                "dailyInterestRate": "0.00007"
            }
        ]
    }
}
```

