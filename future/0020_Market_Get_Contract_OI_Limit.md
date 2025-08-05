---
conversion_date: "2025-03-14"
document_title: "Get Contract OI Limit | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Contracts-Oi"
---

# Get Contract OI Limit | Bitget API

## Get Contract OI Limit

**Rate Limit:** 10 req/sec/IP

### Description

Interface is used to get future contract OI Limit.

### HTTP Request

```
GET /api/v2/mix/market/oi-limit
```

### Request Parameters

| Parameter     | Type   | Required | Description                                              |
|---------------|--------|----------|----------------------------------------------------------|
| symbol        | String | No       | Trading pair, based on the symbolName, i.e. BTCUSDT      |
| productType   | String | Yes      | Product type:<br>**USDT-FUTURES** – USDT professional futures<br>**COIN-FUTURES** – Mixed futures<br>**USDC-FUTURES** – USDC professional futures |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/market/oi-limit?productType=usdt-futures&symbol=BTCUSDT"
```

### Response Parameters

| Parameter            | Type   | Description                                             |
|----------------------|--------|---------------------------------------------------------|
| > symbol             | String | Product name                                            |
| > notionalValue      | String | Individual User Position Notional Value                |
| > totalNotionalValue | String | Sub-account and Main-account Position Notional Value   |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1741596239587,
    "data": [
        {
            "symbol": "BTCUSDT",
            "notionalValue": "100000",
            "totalNotionalValue": "200000"
        },
        {
            "symbol": "BCHUSDT",
            "notionalValue": "100000",
            "totalNotionalValue": "200000"
        }
    ]
}
```

