---
conversion_date: "2025-03-20"
document_title: "Modify Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Modify-Order"
---

# Modify Order | Bitget API

## Modify Order

**Speed limit is 10 times/s for average users. Frequency limit imposed according to user ID**

### Description

Interface for order modification, used to modify a pending order, such as its TP/SL and/or price/size.

- Modifying size and price will cancel the old order; then create a new order asynchronously, modify the preset TPSL will not cancel the old order.
- Modifying size and price, please pass in both, not just one of them
- Modify the order price, size and preset TPSL according to orderId or clientOId
- It is only allowed to modify the new status limit order. If the size, price and TPSL all is set in the request, then the TPSL will not work
- Modify the limit order price and size, please be sure to provide newClientOid, because the orderId of the new order cannot be returned synchronously, so you need to use newClientOid to help you query order information
- Modifying the order size needs to meet the minimum order quantity
- If you only modify the TPSL, please do not pass price and size. If you only pass one of TP or SL, the other one will be cancelled

### HTTP Request

```
POST /api/v2/mix/order/modify-order
```

### Request Parameters

| Parameter | Type   | Required | Description |
|----------|--------|----------|-------------|
| orderId | String | No | Order ID. Either orderId or clientOid is required. If both are entered, orderId prevails. |
| clientOid | String | No | Customize order ID. Either orderId or clientOid is required. If both are entered, orderId prevails. |
| symbol | String | Yes | Trading pair, e.g. ETHUSDT |
| productType | String | Yes | Product type: <br> - USDT-FUTURES: USDT professional futures <br> - COIN-FUTURES: Mixed futures <br> - USDC-FUTURES: USDC professional futures <br> - SUSDT-FUTURES: USDT professional futures demo <br> - SCOIN-FUTURES: Mixed futures demo <br> - SUSDC-FUTURES: USDC professional futures demo |
| newClientOid | String | Yes | New customized order ID after order modification |
| newSize | String | No | Amount of the modified transaction. The amount stays unchanged if the field is left blank. |
| newPrice | String | No | Modified price for placing new orders. <br> 1. When the existing order type is Limit, the original price will be maintained if the field is left empty. <br> 2. When the existing order type is Limit market, the field should not be set. |
| newPresetStopSurplusPrice | String | No | Modifying take-profit. <br> 1. If the original order has take-profit set and the field is empty, the original value will be kept. <br> 2. If the original order has take-profit set and the field is filled in with a value, TP will be updated; if the original order has take-profit set and the field is not set, a new take-profit value will be added. <br> If there was a TP value and a 0 is filled in the field, the existing TP will be deleted. |
| newPresetStopLossPrice | String | No | Modifying stop-loss. <br> 1. If the original order has stop-loss set and the field is empty, the original value will be kept. <br> 2. If the original order has stop-loss set and the field is filled in with a value, SL will be updated; if the original order has stop-loss set and the field is not set, a new stop-loss value will be added. <br> If there was a SL value and a 0 is filled in the field, the existing SL will be deleted. |

### Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/modify-order" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{ "orderId": "1", "newClientOid": "1212112121223", "symbol": "ETHUSDT", "productType": "usdt-futures", "marginCoin": "USDT", "newSize": "0.04", "newPrice": "1800.00" }'
```

### Return Parameter

| Parameter | Type   | Description |
|----------|--------|-------------|
| orderId | String | Order ID |
| clientOid | String | Customize order ID |

### Response Example

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
