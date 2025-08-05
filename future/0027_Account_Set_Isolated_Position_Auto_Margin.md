---
conversion_date: "2025-03-18"
document_title: "Set Isolated Position Auto Margin | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Set-Auto-Margin"
---

# Set Isolated Position Auto Margin

**Frequency limit:** 5 times/1s (uid)

## Description
Adjust isolated position auto margin

## HTTP Request
```
POST /api/v2/mix/account/set-auto-margin
```

## Request Parameters
| Parameter   | Type   | Required | Description                                                 |
|------------|--------|----------|-------------------------------------------------------------|
| symbol     | String | Yes      | Trading pair                                                |
| autoMargin | String | Yes      | Auto margin flag<br>on — auto margin on<br>off — auto margin off |
| marginCoin | String | Yes      | Margin coin must be capitalized                             |
| holdSide   | String | Yes      | Position direction (no need in cross margin mode).<br>long — long position; short — short position |

## Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/account/set-auto-margin"    -H "ACCESS-KEY:*******"    -H "ACCESS-SIGN:*"    -H "ACCESS-PASSPHRASE:*"    -H "ACCESS-TIMESTAMP:1659076670000"    -H "locale:en-US"    -H "Content-Type: application/json"    -d '{"symbol": "btcusdt","autoMargin": "on","marginCoin": "usdt","holdSide": "long"}'
```

## Response Parameters
| Parameter     | Type   | Description                                  |
|--------------|--------|----------------------------------------------|
| code         | String | ‘00000’: success; others: fail                |

## Response Example
```json
{
    "code": "00000",
    "data": "success",
    "msg": "success",
    "requestTime": 1627293357336
}
```

