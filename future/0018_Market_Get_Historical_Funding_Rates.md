---
conversion_date: "2025-03-14"
document_title: "Get Historical Funding Rates | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-History-Funding-Rate"
---

# Get Historical Funding Rates | Bitget API

## Get Historical Funding Rates

**Frequency limit:** 20 times/1s (IP)

### Description
Get the historical funding rate of the contract

### HTTP Request
```
GET /api/v2/mix/market/history-fund-rate
```

### Request Parameters
| Parameter    | Type   | Required | Description                                                                 |
|-------------|--------|----------|-----------------------------------------------------------------------------|
| symbol      | String | Yes      | Trading pair                                                               |
| productType | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| pageSize    | String | No       | Number of queries: Default: 20, maximum: 100                               |
| pageNo      | String | No       | Page number                                                                |

### Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/history-fund-rate?symbol=BTCUSDT&productType=usdt-futures"
```

### Response Parameters
| Parameter     | Type   | Description         |
|---------------|--------|---------------------|
| symbol        | String | Trading pair name   |
| fundingRate   | String | Funding rate        |
| fundingTime   | String | Settlement time     |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695796546319,
    "data": [
        {
            "symbol": "BTCUSDT",
            "fundingRate": "0.0005",
            "fundingTime": "1695776400000"
        },
        {
            "symbol": "BTCUSDT",
            "fundingRate": "0.000013",
            "fundingTime": "1695715200000"
        }
    ]
}
```

