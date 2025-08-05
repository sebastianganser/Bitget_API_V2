---
conversion_date: "2025-03-20"
document_title: "Batch Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Batch-Order"
---

# Batch Order | Bitget API

## Batch Order

**Rate limit:** 5 requests/second/UID  
**Rate limit:** 1 request/second/UID for copy trading traders

### Description
Supports TP/SL feature. If the current underlying asset does not exist in the position, it is intended to preset the TP/SL. If the current underlying exists in the position, it is intended to modify the TP/SL.  
Ignore the `tradeSide` parameter when position mode is in `one-way-mode`.

### HTTP Request
```
POST /api/v2/mix/order/batch-place-order
```

### Request Parameters
| Parameter | Type | Required | Description |
|----------|------|----------|-------------|
| symbol | String | Yes | Trading pair |
| productType | String | Yes | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| marginCoin | String | Yes | Margin coin, must be capitalized |
| marginMode | String | Yes | Position mode:<br>- isolated: isolated margin<br>- crossed: crossed margin |
| orderList | List<String> | Yes | Order list, maximum length: 50 |
| > size | String | Yes | Amount |
| > price | String | No | Price of the order. Required if the order type is limit |
| > side | String | Yes | Order direction:<br>- buy: Buy<br>- sell: Sell |
| > tradeSide | String | No | Direction, only required in hedge-mode. <br>Open and Close Notes:<br>- Open long: side="buy"; tradeSide="open"<br>- Open short: side="sell"; tradeSide="open"<br>- Close long: side="buy"; tradeSide="close"<br>- Close short: side="sell"; tradeSide="close" |
| > orderType | String | Yes | Order type:<br>- limit: limit orders<br>- market: market orders |
| > force | String | No | Order expiration date. Required if orderType is limit, default value is `gtc`:<br>- ioc: Immediate or cancel<br>- fok: Fill or kill<br>- gtc: Good till canceled<br>- post_only: Post only |
| > clientOid | String | No | Custom order ID |
| > reduceOnly | String | No | Whether or not to just reduce the position:<br>- YES, NO (Default: NO). Applicable only in `one-way-position` mode |
| > presetStopSurplusPrice | String | No | Take-profit value. No take-profit is set if the field is empty |
| > presetStopLossPrice | String | No | Stop-loss value. No stop-loss is set if the field is empty |
| > stpMode | String | No | STP Mode (default: none):<br>- none: not setting STP<br>- cancel_taker: cancel taker order<br>- cancel_maker: cancel maker order<br>- cancel_both: cancel both taker and maker orders |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/batch-place-order" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{ 
    "symbol": "BTCUSDT", 
    "productType": "usdt-futures", 
    "marginMode": "crossed", 
    "marginCoin": "USDT", 
    "orderList": [{ 
            "size": "1", 
            "side": "buy", 
            "tradeSide": "open", 
            "orderType": "market", 
            "force": "gtc", 
            "clientOid": "123456", 
            "reduceOnly": "NO", 
            "presetStopSurplusPrice": "20000", 
            "presetStopLossPrice": "10000" 
        } 
    ] 
}'
```

### Response Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| successList | List<Object> | Successful order list |
| > orderId | String | Order ID |
| > clientOid | String | Customize order ID |
| failureList | List<Object> | Failed order list |
| > orderId | String | Order ID |
| > clientOid | String | Customize order ID |
| > errorMsg | String | Failure reason |
| > errorCode | String | Failure code |

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
        "failureList": []
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```
