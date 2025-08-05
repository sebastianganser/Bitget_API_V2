
---
conversion_date: "2025-03-20"
document_title: "Get Historical Position | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/position/Get-History-Position"
---

# Get Historical Position | Bitget API

## Get Historical Position
**Rate Limit:** 20 times/S (uid)

### Description
Check position history (Only check the data within 3 months)

### HTTP Request
```
GET /api/v2/mix/position/history-position
```

### Request Parameter
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | No       | Trading pair |
| productType   | String | No       | Product type, default: USDT-FUTURES. If `symbol` parameter is provided, then this parameter will not take effect. <br> - USDT-FUTURES: USDT professional futures <br> - COIN-FUTURES: Mixed futures <br> - USDC-FUTURES: USDC professional futures <br> - SUSDT-FUTURES: USDT professional futures demo <br> - SCOIN-FUTURES: Mixed futures demo <br> - SUSDC-FUTURES: USDC professional futures demo |
| idLessThan    | String | No       | Requests the content on the page before this ID (older data), the value input should be the endId of the corresponding interface. |
| startTime     | String | No       | Start time (timestamp in milliseconds). For example: 1597026383085. Wildest time range is 3 months; if empty, default is 3 months. |
| endTime       | String | No       | End time (timestamp in milliseconds). For example: 1597026383085. Wildest time range is 3 months; if empty, default is 3 months. |
| limit         | String | No       | Default 20, Max 100 |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/position/history-position?productType=USDT-FUTURES" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameter
| Parameter     | Type   | Description |
|---------------|--------|-------------|
| list          | Array  | Historical Position Data |
| > positionId  | String | History position ID |
| > symbol      | String | Trading pair |
| > marginCoin  | String | Margin coin |
| > holdSide    | String | Position direction: <br> - long: long position <br> - short: short position |
| > openAvgPrice| String | Average price of opening position |
| > closeAvgPrice | String | Average price of closing position |
| > marginMode  | String | Margin Mode: <br> - isolated: Isolated margin <br> - crossed: Cross margin |
| > openTotalPos| String | Accumulated amount of long positions |
| > closeTotalPos| String | Accumulated amount of short positions |
| > pnl         | String | Realized profit and loss |
| > netProfit   | String | Net profit |
| > totalFunding| String | Accumulated funding costs |
| > openFee     | String | Total handling fee for position opening |
| > closeFee    | String | Total handling fee for position closing |
| > uTime       | String | Last update time (Timestamp milliseconds) |
| > cTime       | String | Create time (Timestamp milliseconds) |
| endId         | String | ID of the last data. `id` value is tracking number used for `idLessThan` parameter. |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1312312312321,
    "data": {
        "list": [{
            "positionId": "xxxxxxxxxxx",
            "marginCoin": "USDT",
            "symbol": "BTCUSDT",
            "holdSide": "long",
            "openAvgPrice": "32000",
            "closeAvgPrice": "32500",
            "marginMode": "isolated",
            "openTotalPos": "0.01",
            "closeTotalPos": "0.01",
            "pnl": "14.1",
            "netProfit": "12.1",
            "totalFunding": "0.1",
            "openFee": "0.01",
            "closeFee": "0.01",
            "cTime": "1988824171000",
            "uTime": "1988824171000"
        }],
        "endId": "23423432423423234"
    }
}
```

