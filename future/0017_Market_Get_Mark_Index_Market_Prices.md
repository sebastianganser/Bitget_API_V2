---
conversion_date: "2025-03-14"
document_title: "Get Mark/Index/Market Prices | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Symbol-Price"
---

# Get Mark/Index/Market Prices

**20 times/s, frequency is limited according to user ID**

## Description

Get market/index/mark prices

## HTTP Request

```
GET /api/v2/mix/market/symbol-price
```

## Request Parameters

| Parameter     | Type   | Required | Description                                 |
|---------------|--------|----------|---------------------------------------------|
| symbol        | String | Yes      | Trading pair                                |
| productType   | String | Yes      | Product type                                |

### Product Types

- **USDT-FUTURES**: USDT professional futures  
- **COIN-FUTURES**: Mixed futures  
- **USDC-FUTURES**: USDC professional futures  
- **SUSDT-FUTURES**: USDT professional futures demo  
- **SCOIN-FUTURES**: Mixed futures demo  
- **SUSDC-FUTURES**: USDC professional futures demo  

## Request Example

```
curl "https://api.bitget.com/api/v2/mix/market/symbol-price?productType=usdt-futures&symbol=BTCUSDT"
```

## Response Parameters

| Parameter    | Type   | Description                                         |
|--------------|--------|-----------------------------------------------------|
| symbol       | String | Trading pair name                                   |
| price        | String | Latest price of the exchange                        |
| indexPrice   | String | Index price                                         |
| markPrice    | String | Mark price                                          |
| ts           | String | Milliseconds format of current data timestamp Unix, e.g. 1672410780000 |

## Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695793384294,
    "data": [
        {
            "symbol": "BTCUSDT",
            "price": "26242",
            "indexPrice": "34867",
            "markPrice": "25555",
            "ts": "1695793390482"
        }
    ]
}
```

