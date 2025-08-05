---
conversion_date: "2025-03-28"
document_title: "Get Single Account | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Get-Single-Account"
---

# Get Single Account

**Frequency limit**: 10 times/1s (uid)

## Description

Get account details with the given `marginCoin` and `productType`.

## HTTP Request

```
GET /api/v2/mix/account/account
```

## Request Parameters

| Parameter    | Type   | Required | Description   |
|--------------|--------|----------|---------------|
| symbol       | String | Yes      | Trading pair  |
| productType  | String | Yes      | Product type<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| marginCoin   | String | Yes      | Margin coin   |

## Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/account/account?symbol=btcusdt&productType=USDT-FUTURES&marginCoin=usdt" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters

| Parameter                  | Type   | Description |
|---------------------------|--------|-------------|
| marginCoin                | String | Margin coin |
| locked                    | String | Locked quantity (margin coin). Lockup will be triggered when there is a position to be closed. |
| available                 | String | Available quantity in the account |
| crossedMaxAvailable       | String | Maximum available balance to open positions under the cross margin mode (margin coin) |
| isolatedMaxAvailable      | String | Maximum available balance to open positions under the isolated margin mode (margin coin) |
| maxTransferOut            | String | Maximum transferable amount |
| accountEquity             | String | Account equity (margin coin), including unrealized PnL (based on mark price) |
| usdtEquity                | String | Account equity in USDT |
| btcEquity                 | String | Account equity in BTC |
| crossedRiskRate           | String | Risk ratio in cross margin mode |
| crossedMarginLeverage     | String | Leverage in cross margin mode |
| isolatedLongLever         | String | Leverage of long positions in isolated margin mode |
| isolatedShortLever        | String | Leverage of short positions in isolated margin mode |
| marginMode                | String | Margin mode.<br>isolated – isolated margin mode;<br>crossed – cross margin mode |
| posMode                   | String | Position mode<br>one_way_mode: one-way mode<br>hedge_mode: hedge mode |
| unrealizedPL              | String | Unrealized PnL |
| coupon                    | String | Trading bonus |
| crossedUnrealizedPL       | String | unrealizedPL for crossed |
| isolatedUnrealizedPL      | String | unrealizedPL for isolated |
| assetMode                 | String | Assets mode<br>union: Multi-assets mode<br>single: Single-assets mode |

## Response Example

```json
{
  "code": "00000",
  "data": {
    "marginCoin": "USDT",
    "locked": "0",
    "available": "13168.86110692",
    "crossedMaxAvailable": "13168.86110692",
    "isolatedMaxAvailable": "13168.86110692",
    "maxTransferOut": "13168.86110692",
    "accountEquity": "13178.86110692",
    "usdtEquity": "13178.861106922",
    "btcEquity": "0.344746495477",
    "crossedRiskRate": "0",
    "crossedMarginLeverage": "20",
    "isolatedLongLever": "20",
    "isolatedShortLever": "20",
    "marginMode": "crossed",
    "posMode": "hedge_mode",
    "unrealizedPL": "",
    "coupon": "0",
    "crossedUnrealizedPL": "23",
    "isolatedUnrealizedPL": "0",
    "assetMode": "union"
  },
  "msg": "success",
  "requestTime": 1627292199523
}
```
