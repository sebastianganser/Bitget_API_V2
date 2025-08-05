---
conversion_date: "2025-03-14"
document_title: "Get Ticker | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/market/Get-Ticker"
---

# Get Ticker | Bitget API

**Frequency limit:** 20 times/1s (IP)

## Description
Get ticker data of the given `productType` and `symbol`.

## HTTP Request
```
GET /api/v2/mix/market/ticker
```

## Request Parameters
| Parameter    | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| symbol       | String | Yes      | Trading pair                                     |
| productType  | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/market/ticker?productType=COIN-FUTURES&symbol=ETHUSDM24"
```

## Response Parameters
| Parameter           | Type   | Description                                                                                     |
|--------------------|--------|-------------------------------------------------------------------------------------------------|
| symbol             | String | Trading pair name                                                                               |
| lastPr             | String | Last price                                                                                      |
| askPr              | String | Ask price                                                                                       |
| bidPr              | String | Bid price                                                                                       |
| bidSz              | String | Buying amount                                                                                   |
| askSz              | String | Selling amount                                                                                  |
| high24h            | String | 24h high                                                                                        |
| low24h             | String | 24h low                                                                                         |
| ts                 | String | Milliseconds format of current data timestamp (Unix), e.g. 1597026383085                       |
| change24h          | String | Price increase or decrease (24 hours)                                                           |
| baseVolume         | String | Trading volume of the coin                                                                      |
| quoteVolume        | String | Trading volume of quote currency                                                                |
| usdtVolume         | String | Trading volume of USDT                                                                          |
| openUtc            | String | UTC0 opening price                                                                              |
| changeUtc24h       | String | UTC0 24-hour price increase and decrease                                                        |
| indexPrice         | String | Index price                                                                                     |
| fundingRate        | String | Funding rate                                                                                    |
| holdingAmount      | String | Current holding positions (base coin)                                                           |
| open24h            | String | Entry price of the last 24 hours. Compared on a 24-hour basis.                                 |
| deliveryStartTime  | String | Delivery start time (only for delivery contracts)                                               |
| deliveryTime       | String | Delivery time (only for delivery contracts)                                                     |
| deliveryStatus     | String | Delivery status (only for delivery contracts):<br>- delivery_config_period: Newly listed currency pairs are configured<br>- delivery_normal: Trading normally<br>- delivery_before: 10 minutes before delivery, opening positions are prohibited<br>- delivery_period: Delivery, opening, closing, and canceling orders are prohibited |
| markPrice          | String | Mark price                                                                                      |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695794095685,
    "data": [
        {
            "symbol": "ETHUSD_231229",
            "lastPr": "1829.3",
            "askPr": "1829.8",
            "bidPr": "1829.3",
            "bidSz": "0.054",
            "askSz": "0.785",
            "high24h": "0",
            "low24h": "0",
            "ts": "1695794098184",
            "change24h": "0",
            "baseVolume": "0",
            "quoteVolume": "0",
            "usdtVolume": "0",
            "openUtc": "0",
            "changeUtc24h": "0",
            "indexPrice": "1822.15",
            "fundingRate": "0",
            "holdingAmount": "9488.49",
            "deliveryStartTime": "1693538723186",
            "deliveryTime": "1703836799000",
            "deliveryStatus": "delivery_normal",
            "open24h": "0",
            "markPrice": "1829"
        }
    ]
}
```
