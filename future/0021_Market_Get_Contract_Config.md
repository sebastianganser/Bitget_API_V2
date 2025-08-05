---
conversion_date: "2025-03-14"
document_title: "Get Contract Config | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-All-Symbols-Contracts"
---

# Get Contract Config

**Rate Limit:** 20 req/sec/IP

## Description
Interface is used to get future contract details.

## HTTP Request
```
GET /api/v2/mix/market/contracts
```

## Request Parameters
| Parameter     | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| symbol       | String | No       | Trading pair, based on the symbolName, i.e. BTCUSDT                        |
| productType  | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |

## Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/contracts?productType=usdt-futures&symbol=BTCUSDT"
```

## Response Parameters
| Parameter               | Type            | Description                                                                                       |
|------------------------|------------------|---------------------------------------------------------------------------------------------------|
| symbol                 | String           | Product name                                                                                      |
| baseCoin               | String           | Base currency (e.g., ETH in ETHUSDT)                                                              |
| quoteCoin              | String           | Quote currency (e.g., USDT in ETHUSDT)                                                            |
| buyLimitPriceRatio     | String           | Ratio of bid price to limit price                                                                 |
| sellLimitPriceRatio    | String           | Ratio of ask price to limit price                                                                 |
| feeRateUpRatio         | String           | Transaction fee increase ratio                                                                    |
| makerFeeRate           | String           | Maker rate                                                                                        |
| takerFeeRate           | String           | Taker rate                                                                                        |
| openCostUpRatio        | String           | Opening cost increase ratio                                                                       |
| supportMarginCoins     | List<String>     | Supported margin coins                                                                            |
| minTradeNum            | String           | Minimum opening amount (base currency)                                                            |
| priceEndStep           | String           | Price step length                                                                                 |
| volumePlace            | String           | Decimal places of the quantity                                                                    |
| pricePlace             | String           | Decimal places of the price                                                                       |
| sizeMultiplier         | String           | Quantity multiplier; order quantity must exceed minTradeNum and be a multiple of sizeMultiplier. |
| symbolType             | String           | Futures types: perpetual; delivery                                                                |
| minTradeUSDT           | String           | Minimum USDT transaction amount                                                                   |
| maxSymbolOrderNum      | String           | Maximum number of orders held (symbol dimension)                                                  |
| maxProductOrderNum     | String           | Maximum number of held orders (product type dimension)                                            |
| maxPositionNum         | String           | Maximum number of positions held                                                                  |
| symbolStatus           | String           | Trading pair status:<br>- listed: Listing symbol<br>- normal: Trade normal<br>- maintain: Can't open/close position<br>- limit_open: Can't place orders (can close position)<br>- restrictedAPI: Can't place orders with API<br>- off: Offline |
| offTime                | String           | Removal time; "-1" means normal                                                                   |
| limitOpenTime          | String           | Time to open positions; "-1" means normal                                                         |
| deliveryTime           | String           | Delivery time                                                                                     |
| deliveryStartTime      | String           | Delivery start time                                                                               |
| deliveryPeriod         | String           | Delivery period:<br>- this_quarter: Current quarter<br>- next_quarter: Second quarter             |
| launchTime             | String           | Listing time                                                                                      |
| fundInterval           | String           | Funding fee settlement cycle, hourly/every 8 hours                                                |
| minLever               | String           | Minimum leverage                                                                                  |
| maxLever               | String           | Maximum leverage                                                                                  |
| posLimit               | String           | Position limits                                                                                   |
| maintainTime           | String           | Maintenance time (value appears during maintenance or upcoming maintenance)                       |

## Response Example
```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1695793701269,
  "data": [
    {
      "symbol": "BTCUSDT",
      "baseCoin": "BTC",
      "quoteCoin": "USDT",
      "buyLimitPriceRatio": "0.9",
      "sellLimitPriceRatio": "0.9",
      "feeRateUpRatio": "0.1",
      "makerFeeRate": "0.0004",
      "takerFeeRate": "0.0006",
      "openCostUpRatio": "0.1",
      "supportMarginCoins": ["USDT"],
      "minTradeNum": "0.01",
      "priceEndStep": "1",
      "volumePlace": "2",
      "pricePlace": "1",
      "sizeMultiplier": "0.01",
      "symbolType": "perpetual",
      "minTradeUSDT": "5",
      "maxSymbolOrderNum": "999999",
      "maxProductOrderNum": "999999",
      "maxPositionNum": "150",
      "symbolStatus": "normal",
      "offTime": "-1",
      "limitOpenTime": "-1",
      "deliveryTime": "",
      "deliveryStartTime": "",
      "launchTime": "",
      "fundInterval": "8",
      "minLever": "1",
      "maxLever": "125",
      "posLimit": "0.05",
      "maintainTime": "1680165535278"
    }
  ]
}
```
