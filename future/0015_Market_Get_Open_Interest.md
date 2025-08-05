---
conversion_date: "2025-03-14"
document_title: "Get Open Interest | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Open-Interest"
---

# Get Open Interest

**Frequency limit:** 20 times/1s (IP)

## Description
Get the total positions of a certain trading pair on the platform.

## HTTP Request
```
GET /api/v2/mix/market/open-interest
```

## Request Parameters
| Parameter     | Type   | Required | Description                             |
|--------------|--------|----------|-----------------------------------------|
| symbol       | String | Yes      | Trading pair                            |
| productType  | String | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |

## Request Example
```
curl "https://api.bitget.com/api/v2/mix/market/open-interest?symbol=BTCUSDT&productType=usdt-futures"
```

## Response Parameters
| Parameter         | Type   | Description                                                      |
|------------------|--------|------------------------------------------------------------------|
| ts               | String | Milliseconds format of data time (Unix timestamp), e.g., 1672410780000 |
| openInterestList | String | Open interest data collection                                    |
| → symbol         | String | Trading pair name                                                |
| → size           | String | Total open interest of the platform<br>Specific coins, e.g., ETH in ETHUSDT |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695796780343,
    "data": {
        "openInterestList": [
            {
                "symbol": "BTCUSDT",
                "size": "34278.06"
            }
        ],
        "ts": "1695796781616"
    }
}
```