---
conversion_date: "2025-03-20"
document_title: "Get Historical Transaction Details | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Get-Fill-History"
---

# Get Historical Transaction Details

**Frequency limit:** 10 times/1s (uid)

## Description
Get order fill history

## HTTP Request
```
GET /api/v2/mix/order/fill-history
```

## Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| orderId       | String | No       | Order ID. Either orderId or clientOid is required. If both are entered, orderId prevails. |
| symbol        | String | No       | Trading pair, e.g. ETHUSDT |
| productType   | String | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>It does not support to query the data in demo trading |
| startTime     | String | No       | Start timestamp (Unix timestamp in milliseconds, e.g. 1597026383085).<br>The maximum time span supported is a week. The default end time is a week if no value is set. For Managed Sub-Account, startTime cannot be earlier than the binding time. |
| endTime       | String | No       | End timestamp (Unix timestamp in milliseconds, e.g. 1597026383085).<br>The maximum time span supported is a week. Default start time is a week ago if not set. |
| idLessThan    | String | No       | Requests data before this ID (older data). The value input should be the endId of the corresponding interface. |
| limit         | String | No       | Number of queries: Maximum: 100, default: 100 |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/order/fill-history?productType=usdt-futures" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json"
```

## Response Parameters
| Parameter   | Type   | Description |
|-------------|--------|-------------|
| endId       | String | Last query ended order ID |
| fillList    | List<Object> | Order list |

### fillList Object
| Field              | Type   | Description |
|--------------------|--------|-------------|
| symbol             | String | Trading pair |
| tradeId            | String | Transaction ID |
| orderId            | String | Order ID |
| price              | String | Deal price |
| baseVolume         | String | Amount of coins traded |
| feeDetail          | List<Object> | Transaction fee |
| > deduction        | String | Whether or not to deduct (vouchers) |
| > feeCoin          | String | Crypto ticker |
| > totalDeductionFee| String | Total transaction fee discount |
| > totalFee         | String | Total transaction fee |
| side               | String | Direction (Buy; Sell) |
| quoteVolume        | String | Trading amount in quoting coin |
| profit             | String | Profit |
| enterPointSource   | String | Order source:<br>WEB, API, SYS, ANDROID, IOS |
| tradeSide          | String | Direction:<br>close, open, reduce_close_long, reduce_close_short, burst_close_long, burst_close_short, offset_close_long, offset_close_short, delivery_close_long, delivery_close_short, dte_sys_adl_close_long, dte_sys_adl_close_short, buy_single, sell_single, reduce_buy_single, reduce_sell_single, burst_buy_single, burst_sell_single, delivery_sell_single, delivery_buy_single, dte_sys_adl_buy_in_single_side_mode, dte_sys_adl_sell_in_single_side_mode |
| posMode            | String | Position mode:<br>one_way_mode, hedge_mode |
| tradeScope         | String | Trader tag:<br>taker, maker |
| cTime              | String | Date of transaction |

## Response Example
```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1699267238892,
  "data": {
    "fillList": [
      {
        "tradeId": "xxxx",
        "symbol": "ETHUSDT",
        "orderId": "xxxx",
        "price": "1801.33",
        "baseVolume": "0.02",
        "feeDetail": [
          {
            "deduction": "no",
            "feeCoin": "USDT",
            "totalDeductionFee": "0",
            "totalFee": "-0.02161596"
          }
        ],
        "side": "sell",
        "quoteVolume": "36.0266",
        "profit": "0.0252",
        "enterPointSource": "ios",
        "tradeSide": "sell_single",
        "posMode": "one_way_mode",
        "tradeScope": "taker",
        "cTime": "1698730804882"
      }
    ],
    "endId": "123456789"
  }
}
```