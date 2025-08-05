---
conversion_date: "2025-03-20"
document_title: "Get Order Fill Details | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Get-Order-Fills"
---

# Get Order Fill Details | Bitget API

## Get Order Fill Details
Speed limit is 10 times/s for average users. Frequency limit imposed according to user ID

### Description
Get order fill details

### HTTP Request
```
GET /api/v2/mix/order/fills
```

### Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| orderId       | String | No       | Order ID |
| symbol        | String | No       | Trading pair, e.g. ETHUSDT |
| productType   | String | Yes      | Product type:<br>USDT-FUTURES USDT professional futures<br>COIN-FUTURES Mixed futures<br>USDC-FUTURES USDC professional futures<br>SUSDT-FUTURES USDT professional futures demo<br>SCOIN-FUTURES Mixed futures demo<br>SUSDC-FUTURES USDC professional futures demo |
| idLessThan    | String | No       | Requests the content on the page before the tradeId (older data). |
| startTime     | String | No       | Start time (time stamp in milliseconds). The maximum time span supported is three months. The default end time is three months if no value is set for the end time. (For Managed Sub-Account, the StartTime cannot be earlier than the binding time) |
| endTime       | String | No       | End time (time stamp in milliseconds). The maximum time span supported is three months. The default start time is three months ago if no value is set for the start time. |
| limit         | String | No       | Number of queries: Default: 100, maximum: 100 |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/order/fills?productType=usdt-futures" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json"
```

### Response Parameters
| Parameter  | Type         | Description |
|------------|--------------|-------------|
| fillList   | List<Object> | Transaction details |
| > tradeId  | String       | Transaction id |
| > symbol   | String       | Trading pair |
| > orderId  | String       | Order no. |
| > price    | String       | Order price |
| > baseVolume | String     | Amount of coins traded |
| > feeDetail | String      | Transaction fee |
| >> deduction | String     | Whether or not to deduct (vouchers) |
| >> feeCoin  | String      | Crypto ticker |
| >> totalDeductionFee | String | Total transaction fee discount |
| >> totalFee | String      | Total transaction fee |
| > side     | String       | Type of transaction<br>buy: Buy<br>sell: Sell |
| > quoteVolume | String    | Trading amount in quote currency |
| > profit   | String       | Profit |
| > enterPointSource | String | Order source:<br>WEB: Orders created on the website<br>API: Orders created on API<br>SYS: System managed orders<br>ANDROID: Orders from Android app<br>IOS: Orders from iOS app |
| > tradeSide | String     | Direction:<br>close: Close<br>open: Open<br>reduce_close_long: Liquidate partial long positions<br>reduce_close_short: Liquidate partial short positions<br>burst_close_long: Liquidate long positions<br>burst_close_short: Liquidate short positions<br>offset_close_long: Netting partial long positions<br>offset_close_short: Netting partial short positions<br>delivery_close_long: Delivery long positions<br>delivery_close_short: Delivery short positions<br>dte_sys_adl_close_long: ADL close long<br>dte_sys_adl_close_short: ADL close short<br>buy_single: Buy (one-way mode)<br>sell_single: Sell (one-way mode)<br>reduce_buy_single: Liquidate partial, buy (one-way)<br>reduce_sell_single: Liquidate partial, sell (one-way)<br>burst_buy_single: Liquidate short, buy (one-way)<br>burst_sell_single: Liquidate partial, sell (one-way)<br>delivery_sell_single: Delivery sell (one-way)<br>delivery_buy_single: Delivery buy (one-way)<br>dte_sys_adl_buy_in_single_side_mode: ADL buy (one-way)<br>dte_sys_adl_sell_in_single_side_mode: ADL sell (one-way) |
| > posMode | String        | Position mode:<br>one_way_mode<br>hedge_mode |
| > tradeScope | String     | Trader tag:<br>taker<br>maker |
| > cTime | String         | Date of transaction |
| endId | String           | The final order ID, used with idLessThan/idGreaterThan |

### Response Example
```json
{
  "code": "00000",
  "data": {
    "fillList": [
      {
        "tradeId": "123",
        "symbol": "ethusdt",
        "orderId": "121212",
        "price": "1900",
        "baseVolume": "1",
        "feeDetail": [
          {
            "deduction": "yes",
            "feeCoin": "BGB",
            "totalDeductionFee": "-0.017118519726",
            "totalFee": "-0.017118519726"
          }
        ],
        "side": "buy",
        "quoteVolume": "1902",
        "profit": "102",
        "enterPointSource": "api",
        "tradeSide": "close",
        "posMode": "hedge_mode",
        "tradeScope": "taker",
        "cTime": "1627293509612"
      }
    ],
    "endId": "123"
  },
  "msg": "success",
  "requestTime": 1627293504612
}
```
