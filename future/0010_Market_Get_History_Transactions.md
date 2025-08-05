---
conversion_date: "2025-03-14"
document_title: "Get History Transactions | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Fills-History"
---

# Get History Transactions | Bitget API

**Frequency limit:** 10 times/1s (IP)

## Description
Get transaction records of the last 7 days

## HTTP Request
```
GET /api/v2/mix/market/fills-history
```

## Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | Yes      | Trading pair |
| productType   | String | Yes      | Product type <br> - USDT-FUTURES: USDT professional futures <br> - COIN-FUTURES: Mixed futures <br> - USDC-FUTURES: USDC professional futures <br> - SUSDT-FUTURES: USDT professional futures demo <br> - SCOIN-FUTURES: Mixed futures demo <br> - SUSDC-FUTURES: USDC professional futures demo |
| limit         | String | No       | Number of queries: Default: 500, maximum: 1000 |
| idLessThan    | String | No       | Separate page content before this ID is requested (older data), the value input should be the endId of the corresponding interface. |
| startTime     | String | No       | Start timestamp <br> Unix timestamp in milliseconds format, e.g. 1597026383085 <br> (The maximum time span supported is a week. The default end time is a week if no value is set for the end time.) |
| endTime       | String | No       | End timestamp <br> Unix timestamp in milliseconds format, e.g. 1597026383085 <br> (The maximum time span supported is a week. The default start time is a week ago if no value is set for the start time.) |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/market/fills-history?symbol=BTCUSDT&productType=usdt-futures"
```

## Response Parameters
| Parameter | Type   | Description |
|-----------|--------|-------------|
| tradeId   | String | tradeId, descending order |
| price     | String | Price |
| size      | String | Amount, specific base coin |
| side      | String | Trading direction <br> - sell: Sell <br> - buy: Buy |
| ts        | String | Current data timestamp <br> Unix timestamp in milliseconds format, e.g. 1597026383085 |
| symbol    | String | Trading pair name |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695865481335,
    "data": [
        {
            "tradeId": "1",
            "price": "26372.5",
            "size": "9.25",
            "side": "Sell",
            "ts": "1695865151000",
            "symbol": "BTCUSDT"
        },
        {
            "tradeId": "2",
            "price": "26383",
            "size": "12.12",
            "side": "Buy",
            "ts": "1695865115000",
            "symbol": "BTCUSDT"
        }
    ]
}
```

