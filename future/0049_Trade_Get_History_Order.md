
---
conversion_date: "2025-03-20"
document_title: "Get History Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Get-Orders-History"
---

# Get History Order | Bitget API

## Get History Order
**Rate limit:** 10 req/sec/UID

### Description
Get history order (It only supports to get the data within 90 days. The older data can be downloaded from web)

### HTTP Request
```
GET /api/v2/mix/order/orders-history
```

### Request Parameters
| Parameter      | Type   | Required | Description |
|----------------|--------|----------|-------------|
| orderId        | String | No       | Order ID. If both orderId and clientOid are entered, orderId prevails. |
| clientOid      | String | No       | Customize order ID. If both orderId and clientOid are entered, orderId prevails. |
| symbol         | String | No       | Trading pair, e.g. ETHUSDT |
| productType    | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| idLessThan     | String | No       | Requests the content on the page before this ID (older data), the value input should be the endId of the previous request response |
| orderSource    | String | No       | Order sources:<br>- normal<br>- market<br>- profit_market<br>- loss_market<br>- Trader_delegate<br>- trader_profit<br>- trader_loss<br>- reverse<br>- trader_reverse<br>- profit_limit<br>- loss_limit<br>- liquidation<br>- delivery_close_long<br>- delivery_close_short<br>- pos_profit_limit<br>- pos_profit_market<br>- pos_loss_limit<br>- pos_loss_market |
| startTime      | String | No       | Start timestamp (Unix timestamp in milliseconds format, e.g. 1597026383085). For Managed Sub-Account, the StartTime cannot be earlier than the binding time |
| endTime        | String | No       | End timestamp (Unix timestamp in milliseconds format, e.g. 1597026383085) |
| limit          | String | No       | Number of queries: Maximum: 100, default: 100 |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/order/orders-history?productType=usdt-futures"   -H "ACCESS-KEY:your apiKey"   -H "ACCESS-SIGN:*"   -H "ACCESS-PASSPHRASE:*"   -H "ACCESS-TIMESTAMP:1659076670000"   -H "locale:zh-CN"   -H "Content-Type: application/json"
```

### Response Parameters
| Parameter      | Type   | Description |
|----------------|--------|-------------|
| endId          | String | Last query ended order ID |
| entrustedList  | List<Object> | Order list |

#### entrustedList Object Fields
| Field | Type | Description |
|-------|------|-------------|
| symbol | String | Trading pair |
| size | String | Amount |
| orderId | String | Order ID |
| clientOid | String | Custom id |
| baseVolume | String | Amount of coins traded |
| fee | String | Transaction fee |
| price | String | Order price |
| priceAvg | String | Average order price |
| status | String | Order status:<br>- filled<br>- canceled |
| side | String | Direction:<br>- buy<br>- sell |
| force | String | Order expiration date:<br>- ioc<br>- fok<br>- gtc<br>- post_only |
| totalProfits | String | Total PnL |
| posSide | String | Position direction:<br>- long<br>- short<br>- net |
| marginCoin | String | Margin coin |
| quoteVolume | String | Trading amount in quoting coin |
| leverage | String | Leverage |
| marginMode | String | Margin mode:<br>- isolated<br>- crossed |
| reduceOnly | String | Reduce only:<br>- YES<br>- NO |
| enterPointSource | String | Order source:<br>- WEB<br>- API<br>- SYS<br>- ANDROID<br>- IOS |
| tradeSide | String | Direction:<br>- open<br>- close<br>- reduce_close_long<br>- reduce_close_short<br>- offset_close_long<br>- offset_close_short<br>- burst_close_long<br>- burst_close_short<br>- delivery_close_long<br>- delivery_close_short |
| posMode | String | Position mode:<br>- one_way_mode<br>- hedge_mode |
| orderType | String | Order type:<br>- limit<br>- market |
| orderSource | String | Order sources (same values as request) |
| cTime | String | Creation time |
| uTime | String | Last updated time |
| presetStopSurplusPrice | String | Take profit price |
| presetStopLossPrice | String | Stop loss price |

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
                "fee": "-0.00854",
                "price": "1900",
                "priceAvg": "1903",
                "status": "filled",
                "side": "buy",
                "force": "gtc",
                "totalProfits": "0",
                "posSide": "long",
                "marginCoin": "usdt",
                "quoteVolume": "22001.21",
                "leverage": "20",
                "marginMode": "crossed",
                "enterPointSource": "api",
                "tradeSide": "open",
                "posMode": "hedge_mode",
                "orderType": "limit",
                "orderSource": "normal",
                "cTime": "1627293504612",
                "uTime": "1627293505612",
                "presetStopSurplusPrice": "2001",
                "presetStopLossPrice": "1800"
            }
        ],
        "endId": "123"
    },
    "msg": "success",
    "requestTime": 1627293504612
}
```
