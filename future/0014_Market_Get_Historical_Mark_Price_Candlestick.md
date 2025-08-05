---
conversion_date: "2025-03-14"
document_title: "Get Historical Mark Price Candlestick | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-History-Mark-Candle-Data"
---

# Get Historical Mark Price Candlestick | Bitget API

## Get Historical Mark Price Candlestick

**Frequency limit:** 20 times/1s (IP)

### Description
Get historical mark price candle data

### HTTP Request
```
GET /api/v2/mix/market/history-mark-candles
```

### Request Parameters
| Parameter    | Type   | Required | Description |
|--------------|--------|----------|-------------|
| symbol       | String | Yes      | Trading pair |
| productType  | String | Yes      | Product type<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| granularity  | String | Yes      | K-line particle size:<br>- 1m (1 minute)<br>- 3m (3 minutes)<br>- 5m (5 minutes)<br>- 15m (15 minutes)<br>- 30m (30 minutes)<br>- 1H (1 hour)<br>- 4H (4 hours)<br>- 6H (6 hours)<br>- 12H (12 hours)<br>- 1D (1 day)<br>- 3D (3 days)<br>- 1W (1 week)<br>- 1M (monthly line)<br>- 6Hutc (UTC 6 hour line)<br>- 12Hutc (UTC 12 hour line)<br>- 1Dutc (UTC 1-day line)<br>- 3Dutc (UTC 3-day line)<br>- 1Wutc (UTC weekly line)<br>- 1Mutc (UTC monthly line) |
| startTime    | String | No       | The start time is to query the k-lines after this time.<br>According to the different time granularity, the corresponding time unit must be rounded down to be queried.<br>The millisecond format of the Unix timestamp, e.g. 1672410780000. <br>Request data after this start time (the maximum time query range is 90 days). |
| endTime      | String | No       | The end time is to query the k-lines before this time.<br>According to the different time granularity, the corresponding time unit must be rounded down to be queried.<br>The millisecond format of the Unix timestamp, e.g. 1672410780000.<br>Request data before this end time (the maximum time query range is 90 days). |
| limit        | String | No       | Default: 100, maximum: 200 |

### Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/history-mark-candles?symbol=BTCUSDT&granularity=5m&endTime=1691329771000&limit=100&startTime=1688824171000&productType=usdt-futures"
```

### Response Parameters
| Index       | Type   | Description |
|-------------|--------|-------------|
| index[0]    | String | Milliseconds format of timestamp Unix, e.g. 1597026383085 |
| index[1]    | String | Entry price |
| index[2]    | String | Highest price |
| index[3]    | String | Lowest price |
| index[4]    | String | Exit price (Only include the finished K line data) |
| index[5]    | String | Trading volume of the base coin |
| index[6]    | String | Trading volume of quote currency |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695795362764,
    "data": [
        [
            "1691299500000",
            "29803",
            "29803",
            "29803",
            "29803",
            "0",
            "0"
        ],
        [
            "1691299800000",
            "29803",
            "29803",
            "29803",
            "29803",
            "0",
            "0"
        ]
    ]
}
```

