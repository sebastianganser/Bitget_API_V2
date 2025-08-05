---
conversion_date: "2025-03-24"
document_title: "Cancel Trigger Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Cancel-Plan-Order"
---

# Cancel Trigger Order | Bitget API

## Cancel Trigger Order

**Speed limit is 10 times/s (UID)**

### Description

Interface for cancelling trigger orders, can be used to cancel by `productType`, `symbol` and/or trigger ID list.

All orders that fall under that `productType` and `symbol` will be cancelled.

### HTTP Request

```
POST /api/v2/mix/order/cancel-plan-order
```

### Request Parameters

| Parameter     | Type  | Required | Description |
|---------------|-------|----------|-------------|
| orderIdList   | List  | No       | Trigger order id list. If it is passed, symbol must not be null and must be aligned with symbol/productType/planType. |
| > orderId     | String| No       | Trigger order ID. Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| > clientOid   | String| No       | Customized trigger order ID. Either `orderId` or `clientOid` is required. If both are entered, triggerId prevails. |
| symbol        | String| No       | Trading pair, e.g. ETHUSDT |
| productType   | String| Yes      | Product type:<br> - USDT-FUTURES: USDT professional futures<br> - COIN-FUTURES: Mixed futures<br> - USDC-FUTURES: USDC professional futures<br> - SUSDT-FUTURES: USDT professional futures demo<br> - SCOIN-FUTURES: Mixed futures demo<br> - SUSDC-FUTURES: USDC professional futures demo |
| marginCoin    | String| No       | Margin coin must be capitalized |
| planType      | String| No       | Trigger order type:<br> - `normal_plan`: plan order (default)<br> - `profit_plan`: batch profit order<br> - `loss_plan`: batch loss order<br> - `pos_profit`: position profit order<br> - `pos_loss`: position loss order<br> - `moving_plan`: trailing order |

### Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/cancel-plan-order" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{
  "orderIdList": [
    {
      "orderId": "123",
      "clientOid": "321"
    },
    {
      "orderId": "",
      "clientOid": "666"
    },
    {
      "orderId": "123",
      "clientOid": ""
    }
  ],
  "symbol": "ETHUSDT",
  "productType": "usdt-futures",
  "marginCoin": "USDT"
}'
```

### Response Parameters

| Parameter    | Type           | Description |
|--------------|----------------|-------------|
| successList  | List<Object>   | The collection of successfully cancelled orders. |
| > orderId    | String         | Order ID |
| > clientOid  | String         | Customize order ID |
| failureList  | List<Object>   | The collection of unsuccessfully cancelled orders. |
| > orderId    | String         | Order ID |
| > clientOid  | String         | Customize order ID |
| > errorMsg   | String         | Failure reason |

### Response Example

```json
{
    "code": "00000",
    "data": {
        "successList": [
            {
                "orderId": "121212121212",
                "clientOid": "123"
            },
            {
                "orderId": "123",
                "clientOid": ""
            }
        ],
        "failureList": [
            {
                "orderId": "3",
                "clientOid": "123",
                "errorMsg": "notExistend"
            },
            {
                "orderId": "21221",
                "clientOid": "",
                "errorMsg": "notExistend"
            }
        ]
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```
