---
conversion_date: "2025-03-24"
document_title: "Get Pending Trigger Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/get-orders-plan-pending"
---

# Get Pending Trigger Order

**Rate limit:** 10 req/sec/UID

## Description

Can be used to query one or all current trigger orders.

## HTTP Request

```
GET /api/v2/mix/order/orders-plan-pending
```

## Request Parameters

| Parameter    | Type   | Required | Description |
|--------------|--------|----------|-------------|
| orderId      | String | No       | Trigger order ID. Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| clientOid    | String | No       | Customized trigger order ID. Either `orderId` or `clientOid` is required. If both are entered, `orderId` prevails. |
| symbol       | String | No       | Trading pair, e.g. ETHUSDT |
| planType     | String | Yes      | Trigger order type:<br>- `normal_plan`: average trigger order<br>- `track_plan`: trailing stop order<br>- `profit_loss`: take profit and stop loss orders (including the `profit_plan`, `loss_plan`, `moving_plan`, `pos_profit`, and `pos_loss`) |
| productType  | String | Yes      | Product type:<br>- `USDT-FUTURES`: USDT professional futures<br>- `COIN-FUTURES`: Mixed futures<br>- `USDC-FUTURES`: USDC professional futures<br>- `SUSDT-FUTURES`: USDT professional futures demo<br>- `SCOIN-FUTURES`: Mixed futures demo<br>- `SUSDC-FUTURES`: USDC professional futures demo |
| idLessThan   | String | No       | Requests the content on the page before this ID (older data), the value input should be the `endId` of the corresponding interface. |
| startTime    | String | No       | Start timestamp in Unix milliseconds, e.g. `1597026383085`. Max time span supported is three months. Default end time is three months if not set. |
| endTime      | String | No       | End timestamp in Unix milliseconds, e.g. `1597026383085`. Max time span supported is three months. Default start time is three months ago if not set. |
| limit        | String | No       | Number of queries: Default: 100, maximum: 100 |

## Request Example

```bash
curl -X GET "https://api.bitget.com/api/v2/mix/order/orders-plan-pending?orderId=123&clientOid=1234&planType=profit_loss&productType=USDT-FUTURES" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| entrustedList | List<String> | Order list |

Details in `entrustedList`:

- `planType`: Trigger order type (`normal_plan`, `track_plan`)
- `symbol`: Trading pair
- `size`: Amount
- `orderId`: Trigger order ID
- `clientOid`: Customized trigger order ID
- `price`: Order execute price (doesn't exist for trailing stop orders)
- `executePrice`: Execute Price
- `callbackRatio`: Callback rate (1-10, only for trailing stop orders)
- `triggerPrice`: Trigger price
- `triggerType`: Trigger type (`fill_price`, `mark_price`, `index_price`)
- `planStatus`: Order status (live for current trigger orders)
- `side`: Direction (`Buy`, `Sell`)
- `posSide`: Position direction (`long`, `short`, `net`)
- `marginCoin`: Margin coin
- `marginMode`: Margin mode (`isolated`, `crossed`)
- `enterPointSource`: Order source (`WEB`, `API`, `SYS`)
- `tradeSide`: Direction (`open`, `close`)
- `posMode`: Position mode (`one_way_mode`, `hedge_mode`)
- `orderType`: Order type (`limit`, `market`)
- `orderSource`: Order sources:
  - `normal`
  - `market`
  - `profit_market`
  - `loss_market`
  - `Trader_delegate`
  - `trader_profit`
  - `trader_loss`
  - `trader_reverse`
  - `profit_limit`
  - `loss_limit`
  - `delivery_close_short`
  - `pos_profit_limit`
  - `pos_profit_market`
  - `pos_loss_limit`
  - `pos_loss_market`
- `cTime`: Creation time
- `uTime`: Last updated time
- `stopSurplusExecutePrice`: Take profit execution price
- `stopSurplusTriggerPrice`: Take-profit trigger price
- `stopSurplusTriggerType`: Take-profit trigger type (`fill_price`, `mark_price`, `index_price`)
- `stopLossExecutePrice`: Stop loss execution price
- `stopLossTriggerPrice`: Stop-loss trigger price
- `stopLossTriggerType`: Stop-loss trigger type (`fill_price`, `mark_price`, `index_price`)
- `endId`: Used with `idLessThan`/`idGreaterThan`

## Response Example

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
                "clientOid": "121212",
                "price": "1900",
                "executePrice": "1900",
                "callbackRatio": "",
                "triggerPrice": "1901",
                "triggerType": "mark_price",
                "planStatus": "not_trigger",
                "side": "buy",
                "posSide": "long",
                "marginCoin": "usdt",
                "marginMode": "crossed",
                "enterPointSource": "api",
                "tradeSide": "open",
                "posMode": "hedge_mode",
                "orderType": "limit",
                "orderSource": "normal",
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
