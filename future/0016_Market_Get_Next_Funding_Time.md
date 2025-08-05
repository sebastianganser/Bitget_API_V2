---
conversion_date: "2025-03-14"
document_title: "Get Next Funding Time | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Symbol-Next-Funding-Time"
---

# Get Next Funding Time | Bitget API

## Get Next Funding Time

**Frequency limit:** 20 times/1s (IP)

### Description
Get the next settlement time of the contract and the settlement period of the contract.

### HTTP Request
```
GET /api/v2/mix/market/funding-time
```

### Request Parameters
| Parameter    | Type   | Required | Description                     |
|--------------|--------|----------|---------------------------------|
| symbol       | String | Yes      | Trading pair                    |
| productType  | String | Yes      | Product type                    |

**Product Types:**
- USDT-FUTURES: USDT professional futures
- COIN-FUTURES: Mixed futures
- USDC-FUTURES: USDC professional futures
- SUSDT-FUTURES: USDT professional futures demo
- SCOIN-FUTURES: Mixed futures demo
- SUSDC-FUTURES: USDC professional futures demo

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/market/funding-time?symbol=BTCUSDT&productType=usdt-futures"
```

### Response Parameters
| Parameter         | Type   | Description                     |
|-------------------|--------|---------------------------------|
| symbol            | String | Trading pair name              |
| nextFundingTime   | String | Next settlement time (ms)      |
| ratePeriod        | String | Rate settlement cycle (hours)  |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695796425096,
    "data": [
        {
            "symbol": "BTCUSDT",
            "nextFundingTime": "1695801600000",
            "ratePeriod": "8"
        }
    ]
}
```

