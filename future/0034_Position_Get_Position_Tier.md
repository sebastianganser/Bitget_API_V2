---
conversion_date: "2025-03-20"
document_title: "Get Position Tier | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/position/Get-Query-Position-Lever"
---

# Get Position Tier

**Frequency limit:** 10 times/1s (IP)

## Description
Get the position gradient configuration of a certain trading pair.

## HTTP Request
```
GET /api/v2/mix/market/query-position-lever
```

## Request Parameters
| Parameter    | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| productType  | String | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| symbol       | String | Yes      | Trading pair                                                               |

## Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/query-position-lever?symbol=BTCUSDT&productType=usdt-futures"
```

## Response Parameters
| Parameter         | Type   | Description                                                                                         |
|------------------|--------|-----------------------------------------------------------------------------------------------------|
| symbol           | String | Trading pair name                                                                                  |
| level            | String | Tier                                                                                                |
| startUnit        | String | Minimum value                                                                                      |
| endUnit          | String | Maximum value                                                                                      |
| leverage         | String | Leverage                                                                                           |
| keepMarginRate   | String | Maintenance margin rate: The margin amount corresponds to the position quantity tier. When the margin rate of a position is less than the maintenance margin rate, it will trigger a forced partial liquidation or full liquidation. |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695796884470,
    "data": [
        {
            "symbol": "BTCUSDT",
            "level": "1",
            "startUnit": "0",
            "endUnit": "50000",
            "leverage": "125",
            "keepMarginRate": "0.004"
        },
        {
            "symbol": "BTCUSDT",
            "level": "2",
            "startUnit": "50000",
            "endUnit": "200000",
            "leverage": "100",
            "keepMarginRate": "0.005"
        }
    ]
}
```

