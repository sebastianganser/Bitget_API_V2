---
conversion_date: "2025-03-28"
document_title: "Get Account List | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Get-Account-List"
---

# Get Account List | Bitget API

## Get Account List

**Frequency limit:** 10 times/1s (uid)

### Description

Query all account information under a certain product type.

### HTTP Request

```
GET /api/v2/mix/account/accounts
```

### Request Parameters

| Parameter    | Type   | Required | Description |
|--------------|--------|----------|-------------|
| productType  | String | Yes      | Product type<br>USDT-FUTURES USDT professional futures<br>COIN-FUTURES Mixed futures<br>USDC-FUTURES USDC professional futures<br>SUSDT-FUTURES USDT professional futures demo<br>SCOIN-FUTURES Mixed futures demo<br>SUSDC-FUTURES USDC professional futures demo |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/account/accounts?productType=USDT-FUTURES" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" 
```

### Response Parameters

| Parameter                  | Type   | Description |
|----------------------------|--------|-------------|
| marginCoin                | String | Margin coin |
| locked                    | String | Locked quantity (margin coin) |
| available                 | String | Available quantity in the account |
| crossedMaxAvailable       | String | Maximum available balance to open positions under the cross margin mode (margin coin) |
| isolatedMaxAvailable      | String | Maximum available balance to open positions under the isolated margin mode (margin coin) |
| maxTransferOut            | String | Maximum transferable amount |
| accountEquity             | String | Account equity (margin coin), includes unrealized PnL (based on mark price) |
| usdtEquity                | String | Account equity in USDT |
| btcEquity                 | String | Account equity in BTC |
| crossedRiskRate           | String | Risk ratio in cross margin mode |
| unrealizedPL              | String | Unrealized PnL |
| coupon                    | String | Trading bonus |
| unionTotalMargin          | String | Multi-assets |
| unionAvailable            | String | Total available |
| unionMm                   | String | Maintenance margin |
| assetList                 | List   | Asset list |
| ├─ coin                   | String | Asset |
| ├─ balance                | String | Balance |
| └─ available              | String | Maximum transferable amount<br>Unit: current coin |
| isolatedMargin            | String | Isolated Margin Occupied |
| crossedMargin             | String | Crossed Margin Occupied |
| crossedUnrealizedPL       | String | unrealizedPL for crossed |
| isolatedUnrealizedPL      | String | unrealizedPL for isolated |
| assetMode                 | String | Assets mode<br>union: Multi-assets mode<br>single: Single-assets mode |

### Response Example

```json
{
    "code": "00000",
    "data": [
        {
            "marginCoin": "USDT",
            "locked": "0.31876482",
            "available": "10575.26735771",
            "crossedMaxAvailable": "10580.56434289",
            "isolatedMaxAvailable": "10580.56434289",
            "maxTransferOut": "10572.92904289",
            "accountEquity": "10582.90265771",
            "usdtEquity": "10582.902657719473",
            "btcEquity": "0.204885807029",
            "crossedRiskRate": "0",
            "unrealizedPL": "",
            "coupon": "0",
            "unionTotalMagin": "111,1",
            "unionAvailable": "1111.1",
            "unionMm": "111",
            "assetList": [
                {
                    "coin": "BTC",
                    "balance": "1.2",
                    "available": "1.2"
                }
            ],
            "isolatedMargin": "23.43",
            "crossedMargin": "34.34",
            "crossedUnrealizedPL":"23",
            "isolatedUnrealizedPL":"0",
            "assetMode": "union"
        }
    ],
    "msg": "success",
    "requestTime": 1630901215622
}
```