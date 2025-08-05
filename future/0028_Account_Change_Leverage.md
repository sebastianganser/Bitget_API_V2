---
conversion_date: "2025-03-18"
document_title: "Change Leverage | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Change-Leverage"
---

# Change Leverage | Bitget API

## Change Leverage
**Frequency limit:** 5 times/1s (uid)

### Description
Adjust the leverage on the given symbol and productType

### HTTP Request
```
POST /api/v2/mix/account/set-leverage
```

### Request Parameters
| Parameter     | Type   | Required | Description                                                                                                                                                             |
|--------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| symbol       | String | Yes      | Trading pair                                                                                                                                                            |
| productType  | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| marginCoin   | String | Yes      | Margin coin must be capitalized                                                                                                                                         |
| leverage     | String | Yes      | Leverage                                                                                                                                                                |
| holdSide     | String | No       | Position direction:<br>- long: long position<br>- short: short position<br>In crossed Margin, the holdSide parameter is not required.<br>In Isolated Margin, for one_way_mode, the holdSide parameter is not required. For hedge_mode, the holdSide parameter is required. |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/account/set-leverage" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"symbol":"btcusdt","productType":"USDT-FUTURES","marginCoin":"usdt","leverage":"20","holdSide":"long"}'
```

### Response Parameters
| Parameter              | Type   | Description                       |
|-----------------------|--------|-----------------------------------|
| symbol                | String | Trading pair name                |
| marginCoin            | String | Margin coin                      |
| longLeverage          | String | Leverage of long positions       |
| shortLeverage         | String | Leverage of short positions      |
| crossMarginLeverage   | String | Leverage of 'crossed' margin mode|
| marginMode            | String | Margin mode:<br>- isolated – isolated margin mode<br>- crossed – cross margin mode |

### Response Example
```json
{
    "code": "00000",
    "data": {
        "symbol": "BTCUSDT",
        "marginCoin": "USDT",
        "longLeverage": "25",
        "shortLeverage": "20",
        "crossMarginLeverage": "20",
        "marginMode": "crossed"
    },
    "msg": "success",
    "requestTime": 1627293049406
}
```

