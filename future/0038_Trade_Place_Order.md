---
conversion_date: "2025-03-20"
document_title: "Place Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Place-Order"
  - "https://www.bitget.com/api-doc/contract/market/Get-All-Symbols-Contracts"
---

# Place Order | Bitget API

**Rate limit:** 10 requests/second/UID  
**Rate limit:** 1 request/second/UID for copy trading traders

## Description

- Ignore the `tradeSide` parameter when position mode is in *one-way-mode*.
- In *hedge-mode*, when there is a limit close order occupying the position, if the size of the next market close order and limit close orders exceeds the position size, it will return an "insufficient position error" instead of canceling the current limit order and executing the market order.
- Hedge position mode:
  - Open long: `side`=buy, `tradeSide`=open
  - Close long: `side`=buy, `tradeSide`=close
  - Open short: `side`=sell, `tradeSide`=open
  - Close short: `side`=sell, `tradeSide`=close
- One-way position mode:
  - `side`=buy and sell, `tradeSide`: ignore
- In *one-way-mode* position mode, if the total size of the new reduce-only order and the existing reduce-only orders exceeds the position size, the system will cancel the existing reduce-only orders sequentially based on their creation order until the total size of the new and existing reduce-only orders is less than or equal to the position size. Additionally, the response for the latest reduce-only order request will not include an `orderId`. You can use the `clientOid` set in the request to query order details or retrieve the `orderId` from the current pending orders.

## HTTP Request

```
POST /api/v2/mix/order/place-order
```

## Request Parameters

| Parameter | Type | Required | Description |
|----------|------|----------|-------------|
| symbol | String | Yes | Trading pair, e.g. ETHUSDT |
| productType | String | Yes | Product type:  <br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| marginMode | String | Yes | Position mode:<br>isolated: isolated margin<br>crossed: crossed margin |
| marginCoin | String | Yes | Margin coin (capitalized) |
| size | String | Yes | Amount (base coin)<br>To get the decimal places of size: Get Contract Config |
| price | String | No | Price of the order.<br>Required if the "orderType" is limit<br>To get the decimal places of size: Get Contract Config |
| side | String | Yes | Trade side:<br>buy: Buy (one-way-mode); Long position direction (hedge-mode)<br>sell: Sell (one-way-mode); Short position direction (hedge-mode) |
| tradeSide | String | No | Trade type<br>Only required in hedge-mode:<br>open: Open position<br>close: Close position |
| orderType | String | Yes | Order type:<br>limit: limit orders<br>market: market orders |
| force | String | No | Order expiration date.<br>Required if the orderType is limit:<br>ioc: Immediate or cancel<br>fok: Fill or kill<br>gtc: Good till canceled (default value)<br>post_only: Post only |
| clientOid | String | No | Customize order ID |
| reduceOnly | String | No | Whether or not to just reduce the position: YES, NO<br>Default: NO.<br>Applicable only in one-way-position mode |
| presetStopSurplusPrice | String | No | Take-profit value<br>No take-profit is set if the field is empty. |
| presetStopLossPrice | String | No | Stop-loss value<br>No stop-loss is set if the field is empty. |
| stpMode | String | No | STP Mode (Self Trade Prevention):<br>none: not setting STP (default value)<br>cancel_taker: cancel taker order<br>cancel_maker: cancel maker order<br>cancel_both: cancel both of taker and maker orders |

## Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/place-order" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{
    "symbol": "ETHUSDT",
    "productType": "USDT-FUTURES",
    "marginMode": "isolated",
    "marginCoin": "USDT",
    "size": "0.1",
    "price": "2000",
    "side": "sell",
    "tradeSide": "open",
    "orderType": "limit",
    "force": "gtc",
    "clientOid": "121211212122"
  }'
```

## Response Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| orderId | String | Order ID |
| clientOid | String | Customize order ID |

## Response Example

```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1695806875837,
  "data": {
    "clientOid": "121211212122",
    "orderId": "121211212122"
  }
}
```