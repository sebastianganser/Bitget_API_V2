---
conversion_date: "2025-03-20"
document_title: "Simultaneous Stop-profit and Stop-loss Plan Orders | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Place-Pos-Tpsl-Order"
---

# Simultaneous Stop-profit and Stop-loss Plan Orders | Bitget API

## Description
Speed limit is 10 times/s (UID)

Place a stop-profit and stop-loss plan order

## HTTP Request
```
POST /api/v2/mix/order/place-pos-tpsl
```

## Request Parameters
| Parameter                  | Type   | Required | Description                                                                 |
|---------------------------|--------|----------|-----------------------------------------------------------------------------|
| marginCoin                | String | Yes      | Margin currency                                                             |
| productType               | String | Yes      | Product type: <br>usdt-futures: USDT professional futures <br>coin-futures: Mixed futures <br>usdc-futures: USDC professional futures <br>susdt-futures: USDT professional futures demo <br>scoin-futures: Mixed futures demo <br>susdc-futures: USDC professional futures demo |
| symbol                    | String | Yes      | Trading pair, e.g. ETHUSDT                                                  |
| stopSurplusTriggerPrice  | String | Yes      | Take Profit Trigger price                                                   |
| stopSurplusTriggerType   | String | No       | Take Profit Trigger type:<br>fill_price: market price;<br>mark_price: mark price |
| stopSurplusExecutePrice  | String | No       | Take Profit Execution price. <br>If it is 0 or not filled in, it means market price execution. If greater than 0, it means limit price execution. |
| stopLossTriggerPrice     | String | Yes      | Stop Loss Trigger price                                                     |
| stopLossTriggerType      | String | No       | Stop Loss Trigger type:<br>fill_price: market price;<br>mark_price: mark price |
| stopLossExecutePrice     | String | No       | Stop Loss Execution price. <br>If it is 0 or not filled in, it means market price execution. If greater than 0, it means limit price execution. |
| holdSide                 | String | Yes      | Two-way position: (long: long position, short: short position)<br>One-way position: (buy: long position, sell: short position) |
| stpMode                  | String | No       | STP Mode, default: `none` <br>Options:<br>none: not setting STP<br>cancel_taker: cancel taker order<br>cancel_maker: cancel maker order<br>cancel_both: cancel both of taker and maker orders |

## Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/place-pos-tpsl" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{
        "marginCoin": "USDT",
        "productType": "usdt-futures",
        "symbol": "BTCUSDT",
        "stopSurplusTriggerPrice": "69000",
        "stopSurplusTriggerType": "mark_price",
        "stopSurplusExecutePrice": "69001",
        "stopLossTriggerPrice": "55001",
        "stopLossTriggerType": "mark_price",
        "stopLossExecutePrice": "55000",
        "holdSide": "long"
}'
```

## Response Parameters
| Parameter | Type   | Description        |
|-----------|--------|--------------------|
| orderId   | String | Trigger order ID   |

## Response Example
```json
{
    "code": "00000",
    "data": [
        {
            "orderId": "xxxxxxxxxxx"
        },
        {
            "orderId": "xxxxxxxxxxx"
        }
    ],
    "msg": "success",
    "requestTime": 1627293504612
}
```

