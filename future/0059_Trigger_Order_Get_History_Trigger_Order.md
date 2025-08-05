---
conversion_date: "2025-03-24"
document_title: "Get History Trigger Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/orders-plan-history"
---

# Get History Trigger Order

**Speed limit:** 10 times/s (UID)

### Description

Can be used to query one or all previous common orders and trigger orders.

---

### HTTP Request

```
GET /api/v2/mix/order/orders-plan-history
```

---

### Request Parameters

| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| orderId       | String | No       | Order ID<br>Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| clientOid     | String | No       | Customize order ID<br>Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| planType      | String | Yes      | Order type<br>`normal_plan`: trigger order<br>`track_plan`: trailing stop order<br>`profit_loss`: take profit and stop loss orders (including `profit_plan`, `loss_plan`, `moving_plan`, `pos_profit` and `pos_loss`) |
| planStatus    | String | No       | Trigger order status<br>If not specified, all states will be queried:<br>- `executed`: the order triggered<br>- `fail_execute`: Failed to trigger<br>- `cancelled`: Cancelled |
| symbol        | String | No       | Trading pair, e.g. ETHUSDT |
| productType   | String | Yes      | Product type:<br>`USDT-FUTURES`: USDT professional futures<br>`COIN-FUTURES`: Mixed futures<br>`USDC-FUTURES`: USDC professional futures<br>`SUSDT-FUTURES`: USDT professional futures demo<br>`SCOIN-FUTURES`: Mixed futures demo<br>`SUSDC-FUTURES`: USDC professional futures demo |
| idLessThan    | String | No       | Requests the content on the page before this ID (older data), the value input should be the `endId` of the corresponding interface. |
| startTime     | String | No       | Start timestamp (Unix in ms), e.g. 1597026383085<br>(Max time span is 3 months. If `endTime` not set, defaults to 3 months ago.)<br>(For Managed Sub-Account, startTime cannot be earlier than binding time) |
| endTime       | String | No       | End timestamp (Unix in ms), e.g. 1597026383085<br>(Max time span is 3 months. If `startTime` not set, defaults to 3 months ago.) |
| limit         | String | No       | Number of queries: Default: 100, maximum: 100 |

---

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/order/orders-plan-history?planType=normal_plan&symbol=ETHUSDT&productType=usdt-futures" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

---

### Response Parameters

| Parameter      | Type         | Description |
|----------------|--------------|-------------|
| entrustedList  | List<String> | Order list |

Each object in `entrustedList` contains:
- `planType`: Trigger order type (`normal_plan`, `track_plan`)
- `symbol`: Trading pair
- `size`: Amount
- `orderId`: Trigger order ID
- `executeOrderId`: Order ID after plan triggered
- `clientOid`: Customized trigger order ID
- `planStatus`: Order status (`executed`, `fail_execute`, `cancelled`)
- `price`: Order price (not available for trailing stop)
- `executePrice`: Execute price
- `baseVolume`: Amount of coins traded (only when triggered)
- `callbackRatio`: Callback rate (only for trailing stop)
- `triggerPrice`: Trigger price
- `triggerType`: Trigger type (`fill_price`, `mark_price`)
- `side`: Direction (`buy`, `sell`)
- `posSide`: Position direction (`long`, `short`, `net`)
- `marginCoin`: Margin coin
- `marginMode`: Margin mode (`isolated`, `crossed`)
- `enterPointSource`: Order source (`WEB`, `API`, `SYS`, `ANDROID`, `IOS`)
- `tradeSide`: Direction (`open`, `close`)
- `posMode`: Position mode (`one_way_mode`, `hedge_mode`)
- `orderType`: Order type (`limit`, `market`)
- `cTime`: Creation time
- `uTime`: Last updated time
- `stopSurplusExecutePrice`: Take-profit strike price
- `stopSurplusTriggerPrice`: Take-profit trigger price
- `stopSurplusTriggerType`: Take-profit trigger type (`fill_price`, `mark_price`)
- `stopLossExecutePrice`: Stop-loss strike price
- `stopLossTriggerPrice`: Stop-loss trigger price
- `stopLossTriggerType`: Stop-loss trigger type (`fill_price`, `mark_price`)
- `endId`: The last Trigger order ID (used with `idLessThan`/`idGreaterThan`)

---

### Response Example

```json
{
  "code": "00000",
  "data": {
    "entrustedList": [
      {
        "planType": "normal_plan",
        "symbol": "ethusdt",
        "size": "1",
        "orderId": "123",
        "executeOrderId": "123456",
        "clientOid": "",
        "planStatus": "executed",
        "price": "1990",
        "executePrice": "1990",
        "priceAvg": "1999.2",
        "baseVolume": "1",
        "callbackRatio": "",
        "triggerPrice": "1989",
        "triggerType": "fill_price",
        "side": "buy",
        "posSide": "long",
        "marginCoin": "usdt",
        "marginMode": "crossed",
        "enterPointSource": "api",
        "tradeSide": "open",
        "posMode": "hedge_mode",
        "orderType": "limit",
        "cTime": "1627293504612",
        "uTime": "",
        "stopSurplusExecutePrice": "2001",
        "stopSurplusTriggerPrice": "2002",
        "stopSurplusTriggerType": "fill_price",
        "stopLossExecutePrice": "1800",
        "stopLossTriggerPrice": "1820",
        "stopLossTriggerType": "fill_price"
      }
    ],
    "endId": "123"
  },
  "msg": "success",
  "requestTime": 1627293504612
}
```
