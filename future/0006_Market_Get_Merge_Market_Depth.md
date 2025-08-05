---
conversion_date: "2025-03-14"
document_title: "Get Merge Market Depth | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Merge-Depth"
---

# Get Merge Market Depth | Bitget API

## Get Merge Market Depth
**Frequency limit:** 20 times/1s (IP)

### Description
Get merge depth data

### HTTP Request
```
GET /api/v2/mix/market/merge-depth
```

### Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | Yes      | Trading pair |
| productType   | String | Yes      | Product type<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| precision     | String | No       | Price accuracy, according to the selected accuracy as the step size to return the cumulative depth. Enumeration value:<br>- scale0: not merged (default value)<br>- scale1: merged depth of the transaction pair’s quotation accuracy 10<br>- scale2: quotation precision 100<br>- scale3: quotation precision *1000<br>The precision corresponding to 0/1/2/3 is subject to the actual return parameter "scale". The quotation precision of each trading pair is different. If a scale that does not exist is requested, it will be processed according to the maximum available scale. Example: If a trading pair only supports scale0/scale1 and scale2 is requested, it will be reduced to scale1. |
| limit         | String | No       | Fixed gear enumeration value: 1/5/15/50/max. Default gear is 100. Passing "max" returns the maximum gear of the trading pair. If actual depth does not meet the limit, return according to actual gear. "max" returns the maximum level available. |

### Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/merge-depth?productType=usdt-futures&symbol=BTCUSDT"
```

### Response Parameters
| Parameter          | Type           | Description |
|--------------------|----------------|-------------|
| asks               | List<String>   | The selling price elements are price and quantity.<br>- Index 0: Price<br>- Index 1: Quantity |
| bids               | List<String>   | Buying price elements are price and quantity.<br>- Index 0: Price<br>- Index 1: Quantity |
| precision          | String         | Requested precision |
| scale              | String         | Actual precision value |
| isMaxPrecision     | String         | YES indicates current accuracy is the maximum, NO indicates it is not. |
| ts                 | String         | Timestamp |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695870963008,
    "data": {
        "asks": [
            [
                26347.5,
                0.25
            ],
            [
                26348.0,
                0.16
            ]
        ],
        "bids": [
            [
                26346.5,
                0.16
            ],
            [
                26346.0,
                0.32
            ]
        ],
        "ts": "1695870968804",
        "scale": "0.1",
        "precision": "scale0",
        "isMaxPrecision": "NO"
    }
}
```

