---
conversion_date: "2025-03-20"
document_title: "Get Single Position | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/position/get-single-position"
---

# Get Single Position | Bitget API

## Get Single Position

**Rate limit:** 10 requests/sec/UID

### Description
Returns position information of a single symbol, response including estimated liquidation price.

### HTTP Request
```
GET /api/v2/mix/position/single-position
```

### Request Parameters
| Parameter     | Type   | Required | Description |
|--------------|--------|----------|-------------|
| productType  | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| symbol       | String | Yes      | Trading pair, e.g. BTCUSDT |
| marginCoin   | String | Yes      | Margin coin, capitalized, e.g. USDT |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/position/single-position?symbol=btcusdt&productType=USDT-FUTURES&marginCoin=usdt" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameters
| Parameter              | Type   | Description |
|------------------------|--------|-------------|
| symbol                | String | Trading pair name |
| marginCoin            | String | Margin coin |
| holdSide              | String | Position direction:<br>- long: long position<br>- short: short position |
| openDelegateSize      | String | Amount to be filled of the current order (base coin) |
| marginSize            | String | Margin amount (margin coin) |
| available             | String | Available amount for positions (base currency) |
| locked                | String | Frozen amount in the position (base currency) |
| total                 | String | Total amount of all positions (available amount + locked amount) |
| leverage              | String | Leverage |
| achievedProfits       | String | Realized PnL (exclude funding fee and transaction fee) |
| openPriceAvg          | String | Average entry price |
| marginMode            | String | Margin mode:<br>- isolated: isolated margin<br>- crossed: cross margin |
| posMode               | String | Position mode:<br>- one_way_mode: positions in one-way mode<br>- hedge_mode: positions in hedge-mode |
| unrealizedPL          | String | Unrealized PnL |
| liquidationPrice      | String | Estimated liquidation price. If the value <= 0, it means the position is at low risk and there is no liquidation price at this time |
| keepMarginRate        | String | Tiered maintenance margin rate |
| markPrice             | String | Mark price |
| marginRatio           | String | Maintenance margin rate (MMR), 0.1 represents 10% |
| breakEvenPrice        | String | Position breakeven price |
| totalFee              | String | Funding fee, the accumulated value of funding fee during the position. The initial value is empty, indicating that no funding fee has been charged yet. |
| deductedFee           | String | Deducted transaction fees: transaction fees deducted during the position |
| cTime                 | String | Creation time, timestamp, milliseconds |
| assetMode             | String | Asset mode:<br>- single: single asset mode<br>- union: multi-assets mode |
| uTime                 | String | Last updated time, timestamp, milliseconds |
| autoMargin            | String | Auto Margin:<br>- on: Auto Margin Call<br>- off: No Auto Margin Call |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 21312312312321,
    "data": [
        {
            "marginCoin": "USDT",
            "symbol": "BTCUSDT",
            "holdSide": "long",
            "openDelegateSize": "0.01",
            "marginSize": "9.6695050093373343",
            "available": "0.01",
            "locked": "0.09",
            "total": "0.01",
            "leverage": "20",
            "achievedProfits": "0",
            "openPriceAvg": "25000",
            "marginMode": "isolated",
            "posMode": "hedge_mode",
            "unrealizedPL": "1",
            "liquidationPrice": "24144.1124161806977798",
            "keepMarginRate": "0.004",
            "markPrice": "25100",
            "breakEvenPrice": "24778.97",
            "totalFee": "1.45",
            "deductedFee": "0.388",
            "marginRatio": "0.1082149545822005",
            "assetMode": "single",
            "uTime": "1691382137999",
            "autoMargin": "on",
            "cTime": "1691382137448"
        }
    ]
}
```
