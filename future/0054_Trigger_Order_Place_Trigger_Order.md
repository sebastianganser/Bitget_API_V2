---
conversion_date: "2025-03-20"
document_title: "Place Trigger Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Place-Plan-Order"
---

# Place Trigger Order | Bitget API

**Rate limit:** 10 req/sec/UID

## Description
The interface for placing a trigger or trailing stop order with TP/SL setting feature.

## HTTP Request
**POST** `/api/v2/mix/order/place-plan-order`

## Request Parameters
| Parameter | Type | Required | Description |
|----------|------|----------|-------------|
| planType | String | Yes | Trigger order type<br>- `normal_plan`: Trigger order<br>- `track_plan`: Trailing stop order |
| symbol | String | Yes | Trading pair, e.g. `ETHUSDT` |
| productType | String | Yes | Product type:<br>- `USDT-FUTURES`: USDT professional futures<br>- `COIN-FUTURES`: Mixed futures<br>- `USDC-FUTURES`: USDC professional futures<br>- `SUSDT-FUTURES`: USDT professional futures demo<br>- `SCOIN-FUTURES`: Mixed futures demo<br>- `SUSDC-FUTURES`: USDC professional futures demo |
| marginMode | String | Yes | Position mode:<br>- `isolated`: isolated margin<br>- `crossed`: cross margin |
| marginCoin | String | Yes | Margin coin |
| size | String | Yes | Amount (base coin) |
| price | String | No | Price:<br>1. For `track_plan`, it must be empty.<br>2. For `normal_plan`, it is required when `orderType` is `limit`; must be empty when `orderType` is `market`. |
| callbackRatio | String | No | Callback rate (applies to trailing stop orders only).<br>1. Required for trailing stop orders and cannot be greater than 10. |
| triggerPrice | String | Yes | Trigger price |
| triggerType | String | Yes | Trigger type:<br>- `mark_price`: Mark price<br>- `fill_price`: Latest price |
| side | String | Yes | Order direction: `buy` or `sell` |
| tradeSide | String | No | Direction:<br>- `open`: Open<br>- `close`: Close<br>Only required in hedge position mode<br>Notes:<br>- For open long, `side` = `buy`, `tradeSide` = `open`<br>- For open short, `side` = `sell`, `tradeSide` = `open`<br>- For close long, `side` = `buy`, `tradeSide` = `close`<br>- For close short, `side` = `sell`, `tradeSide` = `close` |
| orderType | String | Yes | Order type:<br>- `limit`: limit order<br>- `market`: market order<br>For `track_plan`, it is required and must be `market` |
| clientOid | String | No | Customize order ID |
| reduceOnly | String | No | Whether or not to just reduce the position:<br>- `yes`: Yes<br>- `no`: No (default)<br>Only applicable in buy/sell (one-way position) mode |
| stopSurplusTriggerPrice | String | No | Take-profit trigger price / Take-profit ratio:<br>- `normal_plan`: take-profit trigger price<br>- `track_plan`: take-profit percentage (0.01–999.99)<br>If left empty or 0, no take-profit will be set by default |
| stopSurplusExecutePrice | String | No | Take-profit execute price:<br>- For `track_plan`, must be empty<br>- For `normal_plan`, if `stopSurplusTriggerPrice` is set:<br> - 0 or empty: market order<br> - >0: limit order |
| stopSurplusTriggerType | String | No | Take-profit trigger type:<br>- `fill_price`: Latest price<br>- `mark_price`: Mark price<br>Required if `stopSurplusTriggerPrice` is set<br>For `track_plan`, only `fill_price` accepted |
| stopLossTriggerPrice | String | No | Stop-loss trigger price / Stop-loss ratio:<br>- `normal_plan`: stop-loss trigger price<br>- `track_plan`: stop-loss percentage (0.01–999.99)<br>If left empty or 0, no stop-loss will be set by default |
| stopLossExecutePrice | String | No | Stop-loss execute price:<br>- For `track_plan`, must be empty<br>- For `normal_plan`, if `stopLossTriggerPrice` is set:<br> - 0 or empty: market order<br> - >0: limit order |
| stopLossTriggerType | String | No | Stop-loss trigger type:<br>- `fill_price`: Latest price<br>- `mark_price`: Mark price<br>Required if `stopLossTriggerPrice` is set<br>For `track_plan`, only `fill_price` accepted |
| stpMode | String | No | STP Mode:<br>- `none`: not setting STP (default)<br>- `cancel_taker`: cancel taker order<br>- `cancel_maker`: cancel maker order<br>- `cancel_both`: cancel both taker and maker orders |

## Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/place-plan-order" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{
     "planType":"normal_plan",
     "symbol": "BTCUSDT",
     "productType": "USDT-FUTURES",
     "marginMode": "isolated",
     "marginCoin": "USDT",
     "size": "0.01",
     "price": "24000",
     "callbackRatio": "",
     "triggerPrice": "24100",
     "triggerType": "mark_price",
     "side": "buy",
     "tradeSide": "open",
     "orderType":"limit",
     "clientOid": "121212121212",
     "reduceOnly": "NO",
     "presetStopSurplusPrice": "",
     "stopSurplusTriggerPrice": "",
     "stopSurplusTriggerType": "",
     "presetStopLossPrice": "",
     "stopLossTriggerPrice": "",
     "stopLossTriggerType": ""
   }'
```

## Response Parameters
| Parameter | Type | Description |
|----------|------|-------------|
| orderId | String | Trigger order ID |
| clientOid | String | Customized trigger order ID |

## Response Example
```json
{
    "code": "00000",
    "data": {
        "orderId": "121212121212",
        "clientOid": "BITGET#121212121212"
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```
