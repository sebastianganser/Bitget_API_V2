---
conversion_date: "2025-03-20"
document_title: "Cancel All Orders | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Cancel-All-Orders"
---

# Cancel All Orders | Bitget API

## Cancel All Orders

**Rate limit:** 10 req/sec/UID

### Description

### HTTP Request

`POST /api/v2/mix/order/cancel-all-orders`

### Request Parameters

| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| productType   | String | Yes      | Product type<br>USDT-FUTURES – USDT professional futures<br>COIN-FUTURES – Mixed futures<br>USDC-FUTURES – USDC professional futures<br>SUSDT-FUTURES – USDT professional futures demo<br>SCOIN-FUTURES – Mixed futures demo<br>SUSDC-FUTURES – USDC professional futures demo |
| marginCoin    | String | No       | Margin coin, must be capitalized |
| requestTime   | String | No       | Request Time Unix millisecond timestamp |
| receiveWindow | String | No       | Valid window period Unix millisecond timestamp |

### Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/cancel-all-orders" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{
    "productType": "USDT-FUTURES",
    "marginCoin": "USDT"
}'
```

### Response Parameters

| Parameter     | Type         | Description |
|---------------|--------------|-------------|
| successList   | List<Object> | The collection of successfully cancelled orders. |
| > orderId     | String       | Order ID |
| > clientOid   | String       | Customize order ID |
| failureList   | List<Object> | The collection of unsuccessfully cancelled orders. |
| > orderId     | String       | Order ID |
| > clientOid   | String       | Customize order ID |
| > errorMsg    | String       | Failure reason |
| > errorCode   | String       | Error code |

### Response Example

```json
{
    "code": "00000",
    "data": {
        "successList": [
            {
                "orderId": "121211212122",
                "clientOid": "BITGET#121211212122"
            }
        ],
        "failureList": [
            {
                "orderId": "232",
                "clientOid": "321342",
                "errorMsg": "notExistend"
            }
        ]
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```
