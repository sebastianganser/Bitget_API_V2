---
conversion_date: "2025-03-28"
document_title: "Get Current Funding Rate | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Current-Funding-Rate"
---

# Get Current Funding Rate | Bitget API

## Get Current Funding Rate

**Frequency limit:** 20 times/1s (IP)

### Description

Get the current funding rate of the contract

### HTTP Request

```
GET /api/v2/mix/market/current-fund-rate
```

### Request Parameters

| Parameter    | Type   | Required | Description         |
|--------------|--------|----------|---------------------|
| symbol       | String | Yes      | Trading pair        |
| productType  | String | Yes      | Product type        |

**Product type values:**

- `USDT-FUTURES` – USDT professional futures  
- `COIN-FUTURES` – Mixed futures  
- `USDC-FUTURES` – USDC professional futures  
- `SUSDT-FUTURES` – USDT professional futures demo  
- `SCOIN-FUTURES` – Mixed futures demo  
- `SUSDC-FUTURES` – USDC professional futures demo  

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/market/current-fund-rate?symbol=BTCUSDT&productType=usdt-futures"
```

### Response Parameters

| Parameter              | Type   | Description                                                                 |
|------------------------|--------|-----------------------------------------------------------------------------|
| symbol                 | String | Trading pair name                                                           |
| fundingRate            | String | Current funding rates                                                       |
| fundingRateInterval    | String | Funding rate settlement period<br>Unit: hour. Enumeration values include 1, 2, 4, 8. 1 represents 1 hour, 2 represents 2 hours, and so on. |
| nextUpdate             | String | Next update time<br>Unix timestamp in milliseconds                          |
| minFundingRate         | String | Lower limit of funding rate<br>Returned in decimal form. 0.025 represents 2.5%. |
| maxFundingRate         | String | Upper limit of funding rate<br>Returned in decimal form. 0.025 represents 2.5%. |

### Response Example

```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1743054548546,
  "data": [
    {
      "symbol": "BTCUSDT",
      "fundingRate": "0.000068",
      "fundingRateInterval": "8",
      "nextUpdate": "1743062400000",
      "minFundingRate": "-0.003",
      "maxFundingRate": "0.003"
    }
  ]
}
```

