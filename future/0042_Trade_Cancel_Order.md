---
conversion_date: "2025-03-20"
document_title: "Cancel Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Cancel-Order"
---

# Cancel Order | Bitget API

## Cancel Order
**Frequency limit:** 10 times/1s

### Description
Cancel a pending order

### HTTP Request
```
POST /api/v2/mix/order/cancel-order
```

### Request Parameters
| Parameter    | Type   | Required | Description |
|--------------|--------|----------|-------------|
| symbol       | String | Yes      | Trading pair |
| productType  | String | Yes      | Product type<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| marginCoin   | String | No       | Margin coin must be capitalized |
| orderId      | String | No       | Order ID<br>Either `orderId` or `clientOid` is required. If both are present, `orderId` prevails. |
| clientOid    | String | No       | Customize order ID<br>Either `orderId` or `clientOid` is required. If both are present, `orderId` prevails. |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/cancel-order" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{
    "orderId": "1",
    "symbol": "BTCUSDT",
    "productType": "usdt-futures",
    "marginCoin": "USDT"
}'
```

### Return Parameter
| Parameter  | Type   | Description |
|------------|--------|-------------|
| orderId    | String | Order ID |
| clientOid  | String | Client customized ID |

### Response Example
```json
{
    "code": "00000",
    "data": {
        "orderId": "123",
        "clientOid": ""
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```

