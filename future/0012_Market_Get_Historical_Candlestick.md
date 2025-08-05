
---
conversion_date: "2025-03-14"
document_title: "Get Historical Candlestick | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-History-Candle-Data"
---

# Get Historical Candlestick | Bitget API

## Get Historical Candlestick

**Frequency limit:** 20 times/1s (IP)

### Description
Query all historical K-line data and return a maximum of 200 pieces of data.

### HTTP Request
```
GET /api/v2/mix/market/history-candles
```

### Request Parameters

| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | Yes      | Trading pair |
| productType   | String | Yes      | Product type <br> - USDT-FUTURES: USDT professional futures <br> - COIN-FUTURES: Mixed futures <br> - USDC-FUTURES: USDC professional futures <br> - SUSDT-FUTURES: USDT professional futures demo <br> - SCOIN-FUTURES: Mixed futures demo <br> - SUSDC-FUTURES: USDC professional futures demo |
| granularity   | String | Yes      | K-line particle size <br> - 1m (1 minute) <br> - 3m (3 minutes) <br> - 5m (5 minutes) <br> - 15m (15 minutes) <br> - 30m (30 minutes) <br> - 1H (1 hour) <br> - 4H (4 hours) <br> - 6H (6 hours) <br> - 12H (12 hours) <br> - 1D (1 day) <br> - 3D (3 days) <br> - 1W (1 week) <br> - 1M (monthly line) <br> - 6Hutc (UTC 6 hour line) <br> - 12Hutc (UTC 12 hour line) <br> - 1Dutc (UTC 1-day line) <br> - 3Dutc (UTC 3-day line) <br> - 1Wutc (UTC weekly line) <br> - 1Mutc (UTC monthly line) |
| startTime     | String | No       | The start time is to query the K-lines after this time. The time unit must be rounded down depending on the granularity. <br> Format: milliseconds of Unix timestamp, e.g., 1672410780000. <br> Max time query range: 90 days |
| endTime       | String | No       | The end time is to query the K-lines before this time. The time unit must be rounded down depending on the granularity. <br> Format: milliseconds of Unix timestamp, e.g., 1672410780000. <br> Max time query range: 90 days |
| limit         | String | No       | Default: 100, maximum: 200 |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/market/history-candles?symbol=BTCUSDT&granularity=1W&limit=200&productType=usdt-futures"
```

### Response Parameters

| Parameter   | Type   | Description |
|-------------|--------|-------------|
| index[0]    | String | Milliseconds format of timestamp Unix, e.g., 1597026383085 |
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
    "requestTime": 1695865864944,
    "data": [
        [
            "1687708800000",
            "27176.93",
            "27177.43",
            "27166.93",
            "27177.43",
            "2990.08",
            "81246917.3294"
        ],
        [
            "1688313600000",
            "27177.43",
            "27177.43",
            "24000",
            "24001",
            "2989.1",
            "72450031.0448"
        ]
    ]
}
```
