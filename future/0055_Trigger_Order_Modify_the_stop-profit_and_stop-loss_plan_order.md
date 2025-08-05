---
conversion_date: "2025-03-24"
document_title: "Modify the stop-profit and stop-loss plan order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Modify-Tpsl-Order"
---

# Modify the stop-profit and stop-loss plan order | Bitget API

## Modify the stop-profit and stop-loss plan order

**Speed limit**: 10 times/s (UID)

### Description

Modify the stop-profit and stop-loss plan order

### HTTP Request

```
POST /api/v2/mix/order/modify-tpsl-order
```

### Request Parameters

| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| orderId       | String | No       | Take profit and stop loss order number, 'orderId' and 'clientOid' must provide one |
| clientOid     | String | No       | Take profit and stop loss client order number, 'orderId' and 'clientOid' must provide one |
| marginCoin    | String | Yes      | Margin currency |
| productType   | String | Yes      | Product type<br> - `usdt-futures`: USDT professional futures<br> - `coin-futures`: Mixed futures<br> - `usdc-futures`: USDC professional futures<br> - `susdt-futures`: USDT professional futures demo<br> - `scoin-futures`: Mixed futures demo<br> - `susdc-futures`: USDC professional futures demo |
| symbol        | String | Yes      | Trading pair, e.g. ETHUSDT |
| triggerPrice  | String | Yes      | Trigger price |
| triggerType   | String | No       | Trigger type (`fill_price` = transaction price, `mark_price` = mark price) |
| executePrice  | String | No       | Execution price (if it is 0 or not filled in, it means market price execution. If it is greater than 0, it means limit price execution. When planType (stop-profit and stop-loss type) is `moving_plan` (moving take-profit and stop-loss), it is not filled in and is fixed to the market price.) |
| size          | String | Yes      | Order quantity. For the position take profit and position stop loss orders, the size should be `"size":""` |
| rangeRate     | String | No       | Callback range |

### Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/modify-tpsl-order" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"orderId": "1","clientOid": "2","marginCoin": "USDT","productType": "usdt-futures","symbol": "ethusdt","triggerPrice": "2001","triggerType": "fill_price","executePrice": "0","size": "2","rangeRate": ""}'
```

### Response Parameters

| Parameter  | Type   | Description               |
|------------|--------|---------------------------|
| orderId    | String | Trigger order ID          |
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
