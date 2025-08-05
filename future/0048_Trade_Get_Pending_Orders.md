
---
conversion_date: "2025-03-20"
document_title: "Get Pending Orders | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Get-Orders-Pending"
---

# Get Pending Orders | Bitget API

## Get Pending Orders
**Rate limit:** 10 req/sec/UID

### Description
To query all existing pending orders.

### HTTP Request
```
GET /api/v2/mix/order/orders-pending
```

### Request Parameters
| Parameter      | Type   | Required | Description |
|----------------|--------|----------|-------------|
| orderId        | String | No       | Order ID; If both orderId and clientOid are entered, orderId prevails. |
| clientOid      | String | No       | Customize order ID; If both orderId and clientOid are entered, orderId prevails. |
| symbol         | String | No       | Trading pair, e.g. ETHUSDT |
| productType    | String | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| status         | String | No       | Order status:<br>If not specified, all orders with a status of live (not filled yet) will be returned.<br>live: pending orders<br>partially_filled: Partially filled |
| idLessThan     | String | No       | Requests the content on the page before this ID (older data). The value input should be the endId of the corresponding interface. |
| startTime      | String | No       | Start timestamp (Unix timestamp in milliseconds), e.g. 1597026383085. The maximum time span supported is three months. The default end time is three months if no value is set for the end time. |
| endTime        | String | No       | End timestamp (Unix timestamp in milliseconds), e.g. 1597026383085. The maximum time span supported is three months. The default start time is three months ago if no value is set for the start time. |
| limit          | String | No       | Number of queries: Maximum: 100, default: 100 |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/order/orders-pending?productType=usdt-futures"   -H "ACCESS-KEY:your apiKey"   -H "ACCESS-SIGN:*"   -H "ACCESS-PASSPHRASE:*"   -H "ACCESS-TIMESTAMP:1659076670000"   -H "locale:zh-CN"   -H "Content-Type: application/json"
```

### Response Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| entrustedList | List<Object> | Order list |
| > symbol | String | Trading pair |
| > size | String | Amount |
| > orderId | String | Order ID |
| > clientOid | String | Custom id |
| > baseVolume | String | Amount of coins traded |
| > fee | String | Transaction fee |
| > price | String | Order price |
| > priceAvg | String | Average order price (Empty when status is live) |
| > status | String | Order status:<br>live: Waiting to be filled (not filled yet)<br>partially_filled: Partially filled |
| > side | String | Direction:<br>buy: Buy; sell: Sell |
| > force | String | Order expiration date:<br>ioc (Immediate or cancel), fok (Fill or kill), gtc (Good till canceled), post_only: Post only |
| > totalProfits | String | Total PnL (Empty when status is live) |
| > posSide | String | Position direction:<br>long: two-way long position<br>short: two-way short position<br>net: one-way position |
| > marginCoin | String | Margin coin |
| > quoteVolume | String | Trading amount in quoting coin |
| > leverage | String | Leverage |
| > marginMode | String | Margin mode:<br>isolated: isolated margin<br>crossed: cross margin |
| > reduceOnly | String | Reduce only:<br>YES: yes, NO: no |
| > enterPointSource | String | Order source:<br>WEB: Orders created on the website<br>API: Orders created on API |
| > tradeSide | String | Direction:<br>open (open and close mode)<br>close (open and close mode)<br>reduce_close_long<br>reduce_close_short<br>offset_close_long<br>offset_close_short<br>burst_close_long<br>burst_close_short<br>delivery_close_long<br>delivery_close_short |
| > posMode | String | Position mode:<br>one_way_mode: one-way position<br>hedge_mode: two-way position |
| > orderType | String | Order type:<br>limit: limit order<br>market: market order |
| > orderSource | String | Order sources:<br>normal: Normal order<br>market: market order<br>profit_market: Market TP order<br>loss_market: Market SL order<br>Trader_delegate: Elite trade order<br>trader_profit: Trader takes profit<br>trader_loss: Trader stops loss<br>reverse: Reversed orders<br>trader_reverse: Reversed elite trades<br>profit_limit: Take-profit limit order<br>loss_limit: Stop-loss limit order<br>liquidation: Liquidation order<br>delivery_close_long: close long positions<br>delivery_close_short: close short positions<br>pos_profit_limit: Position take-profit limit order<br>pos_profit_market: Position take-profit market order<br>pos_loss_limit: Position stop-loss limit order<br>pos_loss_market: Position stop-loss market order |
| > cTime | String | Creation time, ms |
| > uTime | String | Last updated time, ms |
| > presetStopSurplusPrice | String | Take Profit Trigger Price |
| > presetStopSurplusType | String | Setting take-profit trigger type:<br>fill_price: filled price<br>mark_price: mark price |
| > presetStopSurplusExecutePrice | String | Take Profit Execution price:<br>If it is 0 or not filled in, it means market price execution. If it is greater than 0, it means limit price execution. |
| > presetStopLossPrice | String | Stop Loss Trigger Price |
| > presetStopLossType | String | Setting stop-loss trigger type:<br>fill_price: filled price<br>mark_price: mark price |
| > presetStopLossExecutePrice | String | Stop Loss Execution price:<br>If it is 0 or not filled in, it means market price execution. If it is greater than 0, it means limit price execution. |
| endId | String | The final order ID. This is used when idLessThan/idGreaterThan is set as a range. |

### Response Example
```json
{
  "code": "00000",
  "data": {
    "entrustedList": [
      {
        "symbol": "ethusdt",
        "size": "100",
        "orderId": "123",
        "clientOid": "12321",
        "baseVolume": "12.1",
        "fee": "",
        "price": "1900",
        "priceAvg": "1903",
        "status": "partially_filled",
        "side": "buy",
        "force": "gtc",
        "totalProfits": "0",
        "posSide": "long",
        "marginCoin": "usdt",
        "quoteVolume": "22001.21",
        "leverage": "20",
        "marginMode": "cross",
        "enterPointSource": "api",
        "tradeSide": "open",
        "posMode": "hedge_mode",
        "orderType": "limit",
        "orderSource": "normal",
        "cTime": "1627293504612",
        "uTime": "1627293505612",
        "presetStopSurplusPrice": "2001",
        "presetStopSurplusType": "mark_price",
        "presetStopSurplusExecutePrice": "2201",
        "presetStopLossPrice": "1800",
        "presetStopLossType": "mark_price",
        "presetStopLossExecutePrice": "1900"
      }
    ],
    "endId": "123"
  },
  "msg": "success",
  "requestTime": 1627293504612
}
```
