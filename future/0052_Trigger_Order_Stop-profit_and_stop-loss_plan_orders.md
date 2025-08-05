---
conversion_date: "2025-03-20"
document_title: "Stop-profit and stop-loss plan orders | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Place-Tpsl-Order"
---

# Stop-profit and stop-loss plan orders | Bitget API

## Description
Speed limit is 10 times/s (UID)

### Place a stop-profit and stop-loss plan order

#### HTTP Request
```
POST /api/v2/mix/order/place-tpsl-order
```

### Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| marginCoin    | String | Yes      | Margin currency (Capitalized) |
| productType   | String | Yes      | Product type:<br> - usdt-futures: USDT professional futures<br> - coin-futures: Mixed futures<br> - usdc-futures: USDC professional futures<br> - susdt-futures: USDT professional futures demo<br> - scoin-futures: Mixed futures demo<br> - susdc-futures: USDC professional futures demo |
| symbol        | String | Yes      | Trading pair, e.g. ETHUSDT |
| planType      | String | Yes      | Take profit and stop loss type:<br> - profit_plan: take profit plan;<br> - loss_plan: stop loss plan;<br> - moving_plan: trailing stop;<br> - pos_profit: position take profit;<br> - pos_loss: position stop loss |
| triggerPrice  | String | Yes      | Trigger price |
| triggerType   | String | No       | Trigger type:<br> - fill_price: market price;<br> - mark_price: mark price |
| executePrice  | String | No       | Execution price:<br> If it is 0 or not filled in, it means market price execution.<br> If it is greater than 0, it means limit price execution.<br> Do not fill in this parameter when planType is moving_plan, it only executes in market price. |
| holdSide      | String | Yes      | Two-way position:<br> - long: long position<br> - short: short position<br> One-way position:<br> - buy: long position<br> - sell: short position |
| size          | String | Yes      | Order quantity (base coin)<br> Required when planType is profit_plan, loss_plan or moving_plan, and should be greater than 0;<br> Not required when planType is pos_profit or pos_loss |
| rangeRate     | String | No       | Callback range<br> Required only when planType is moving_plan |
| clientOid     | String | No       | Customize order ID |
| stpMode       | String | No       | STP Mode, default `none`:<br> - none: not setting STP<br> - cancel_taker: cancel taker order<br> - cancel_maker: cancel maker order<br> - cancel_both: cancel both of taker and maker orders |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/place-tpsl-order" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"marginCoin": "USDT","productType": "usdt-futures","symbol": "ethusdt","planType": "profit_plan","triggerPrice": "2000","triggerType": "mark_price","executePrice": "0","holdSide": "long","size": "1","rangeRate": "","clientOid": "1234"}'
```

### Response Parameters
| Parameter  | Type   | Description |
|------------|--------|-------------|
| orderId    | String | Trigger order ID |
| clientOid  | String | Customized trigger order ID |

### Response Example
```json
{
    "code": "00000",
    "data": {
        "orderId": "121212121212",
        "clientOid": "BITGET#1627293504612"
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```
