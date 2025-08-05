---
conversion_date: "2025-03-24"
document_title: "Modify Trigger Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Modify-Plan-Order"
---

# Modify Trigger Order | Bitget API

## Modify Trigger Order

**Speed limit is 10 times/s (UID)**

### Description

Interface for trigger order modification, used to modify a pending order, such as its TP/SL and/or `triggerPrice`.

### HTTP Request

`POST /api/v2/mix/order/modify-plan-order`

### Request Parameters

| Parameter                        | Type   | Required | Description |
|----------------------------------|--------|----------|-------------|
| orderId                          | String | No       | Trigger order ID. Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| clientOid                        | String | No       | Customized trigger order ID. Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| productType                      | String | Yes      | Product type:<br>- `USDT-FUTURES` USDT professional futures<br>- `COIN-FUTURES` Mixed futures<br>- `USDC-FUTURES` USDC professional futures<br>- `SUSDT-FUTURES` USDT professional futures demo<br>- `SCOIN-FUTURES` Mixed futures demo<br>- `SUSDC-FUTURES` USDC professional futures demo |
| newSize                          | String | No       | Amount of the modified transaction. If empty, amount remains unchanged. |
| newPrice                         | String | No       | Modified price for executing orders.<br>1. For trigger orders of type Limit, the original price remains unchanged if empty. Must be empty for Market orders.<br>2. Must be empty for trailing orders. |
| newCallbackRatio                 | String | No       | Modified callback rate (for trailing stop orders only).<br>1. For trailing stop orders, required and ≤10.<br>2. Must be empty for trigger orders. |
| newTriggerPrice                  | String | No       | Modified trigger price.<br>1. For trigger/trailing stop orders: if not set, stays unchanged; if set, updates. |
| newTriggerType                   | String | No       | Modified trigger type.<br>Requires `newTriggerPrice`.<br>`fill_price`: filled price<br>`mark_price`: mark price |
| newStopSurplusTriggerPrice       | String | No       | Modified take-profit trigger price.<br>1. If empty and original TP set: remains.<br>2. If not empty and TP set: updates.<br>3. If not set and TP not set: adds TP.<br>4. If 0: removes TP. |
| newStopSurplusExecutePrice       | String | No       | Modified take-profit strike price.<br>1. Must be empty for trailing stop orders.<br>2. For trigger orders: if filled, updates; if empty, remains; if 0, removes. |
| newStopSurplusTriggerType        | String | No       | Modified take-profit trigger type (default: transaction price).<br>1. Must be empty for trailing stop orders.<br>2. Required if `newStopSurplusTriggerPrice` is set.<br>`fill_price`, `mark_price` |
| newStopLossTriggerPrice          | String | No       | Modified stop-loss trigger price.<br>1. If empty and SL set: remains.<br>2. If not empty and SL set: updates.<br>3. If not set and SL not set: adds SL.<br>4. If 0: removes SL. |
| newStopLossExecutePrice          | String | No       | Modified stop-loss strike price.<br>1. Must be empty for trailing stop orders.<br>2. For trigger orders: if filled, updates; if empty, remains; if 0, removes. |
| newStopLossTriggerType           | String | No       | Modified stop-loss trigger type (default: transaction price).<br>1. Must be empty for trailing stop orders.<br>2. Required if `newStopLossTriggerPrice` is set. |

### Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/modify-plan-order" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{
        "planType":"normal_plan",
        "orderId": "123",
        "clientOid": "321123",
        "symbol": "ethusdt",
        "productType": "usdt-futures",
        "newSize": "3",
        "newPrice": "2001",
        "newCallbackRatio": "",
        "newTriggerPrice": "2000",
        "newTriggerType": "fill_price",
        "newStopSurplusExecutePrice": "2049",
        "newStopSurplusTriggerPrice": "2050",
        "newStopSurplusTriggerType": "mark_price",
        "newStopLossExecutePrice": "5",
        "newStopLossTriggerPrice": "1970",
        "newStopLossTriggerType": "mark_price"
}'
```

---

### Response Parameters

| Parameter  | Type   | Description                |
|------------|--------|----------------------------|
| orderId    | String | Trigger order ID           |
| clientOid  | String | Customized trigger order ID|

### Response Example

```json
{
    "code": "00000",
    "data": {
        "orderId": "21627293504612",
        "clientOid": "BITGET#1627293504612"
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```

