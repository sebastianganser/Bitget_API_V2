---
conversion_date: "2025-03-14"
document_title: "Get Candlestick Data | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Candle-Data"
---

# Get Candlestick Data | Bitget API

## Get Candlestick Data

**Frequency limit:** 20 times/1s (IP)

### Description
By default, 100 records are returned. If there is no data, an empty array is returned. The queryable data history varies depending on the k-line granularity.

The rules are as follows:
- 1m, 3m, and 5m can be checked for up to one month;
- 15m can be checked for up to 52 days;
- 30m can be searched for up to 62 days;
- 1H can be checked for up to 83 days;
- 2H can be checked for up to 120 days;
- 4H can be checked for up to 240 days;
- 6H can be checked for up to 360 days

### HTTP Request
```
GET /api/v2/mix/market/candles
```

### Request Parameters
| Parameter     | Type   | Required | Description                                                                                     |
|--------------|--------|----------|-------------------------------------------------------------------------------------------------|
| symbol       | String | Yes      | Trading pair                                                                                   |
| productType  | String | Yes      | Product type: <br> USDT-FUTURES (USDT professional futures) <br> COIN-FUTURES (Mixed futures) <br> USDC-FUTURES (USDC professional futures) <br> SUSDT-FUTURES (USDT professional futures demo) <br> SCOIN-FUTURES (Mixed futures demo) <br> SUSDC-FUTURES (USDC professional futures demo) |
| granularity  | String | Yes      | K-line particle size:<br> - 1m (1 minute)<br> - 3m (3 minutes)<br> - 5m (5 minutes)<br> - 15m (15 minutes)<br> - 30m (30 minutes)<br> - 1H (1 hour)<br> - 4H (4 hours)<br> - 6H (6 hours)<br> - 12H (12 hours)<br> - 1D (1 day)<br> - 3D (3 days)<br> - 1W (1 week)<br> - 1M (monthly line)<br> - 6Hutc (UTC 6 hour line)<br> - 12Hutc (UTC 12 hour line)<br> - 1Dutc (UTC 1-day line)<br> - 3Dutc (UTC 3-day line)<br> - 1Wutc (UTC weekly line)<br> - 1Mutc (UTC monthly line) |
| startTime    | String | No       | The start time to query k-lines after this time.<br> Must be rounded down based on granularity.<br> Unix timestamp in milliseconds, e.g., 1672410780000. Max query range: 90 days. |
| endTime      | String | No       | The end time to query k-lines before this time.<br> Must be rounded down based on granularity.<br> Unix timestamp in milliseconds, e.g., 1672410780000. Max query range: 90 days. |
| kLineType    | String | No       | Candlestick chart types: MARKET (default); MARK; INDEX                                       |
| limit        | String | No       | Default: 100, Maximum: 1000                                                                   |

### Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/candles?symbol=BTCUSDT&granularity=5m&limit=100&productType=usdt-futures"
```

### Response Parameters
| Index        | Type   | Description                                                                 |
|--------------|--------|-----------------------------------------------------------------------------|
| index[0]     | String | Milliseconds format of Unix timestamp, e.g., 1597026383085                 |
| index[1]     | String | Entry price                                                                 |
| index[2]     | String | Highest price                                                               |
| index[3]     | String | Lowest price                                                                |
| index[4]     | String | Exit price (latest exit price may be updated). Subscribe to WebSocket to track the latest price. |
| index[5]     | String | Trading volume of the base coin                                             |
| index[6]     | String | Trading volume of quote currency                                            |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695865615662,
    "data": [
        [
            "1695835800000",
            "26210.5",
            "26210.5",
            "26194.5",
            "26194.5",
            "26.26",
            "687897.63"
        ],
        [
            "1695836100000",
            "26194.5",
            "26194.5",
            "26171",
            "26171",
            "17.98",
            "470618.72"
        ]
    ]
}
```
