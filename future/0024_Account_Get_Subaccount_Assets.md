---
conversion_date: "2025-03-28"
document_title: "Get Subaccount Assets | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Get-Sub-Account-Contract-Assets"
---

# Get Subaccount Assets | Bitget API

## Get Subaccount Assets

**Frequency limit:** 1 time/10s (uid)

### Description

Query the contract asset information of all sub-accounts. ND Brokers are not allowed to call this endpoint.

### HTTP Request

```
GET /api/v2/mix/account/sub-account-assets
```

### Request Parameters

| Parameter    | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| productType  | String | Yes      | Product type<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/mix/account/sub-account-assets?productType=USDT-FUTURES" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameters

| Parameter                  | Type   | Description                                                                 |
|---------------------------|--------|-----------------------------------------------------------------------------|
| > userId                  | String | Sub account userId                                                          |
| > assetList               | String | Collection of all futures assets under sub-accounts                         |
| >> marginCoin             | String | Margin coin                                                                 |
| >> locked                 | String | Locked quantity (margin coin)                                               |
| >> available              | String | Available quantity in the account                                           |
| >> crossedMaxAvailable    | String | Maximum available balance to open positions under the cross margin mode    |
| >> isolatedMaxAvailable   | String | Maximum available balance to open positions under the isolated margin mode |
| >> maxTransferOut         | String | Maximum transferable amount                                                 |
| >> equity                 | String | Account equity (margin coin)                                                |
| >> usdtEquity             | String | Account equity in USDT                                                      |
| >> btcEquity              | String | Account equity in BTC                                                       |
| >> unrealizedPL           | String | PnL of open positions                                                       |
| >> coupon                 | String | Trading bonus                                                               |

### Response Example

```json
{
    "code": "00000",
    "data": [
        {
            "userId": 1234567890,
            "assetList": [
                {
                    "marginCoin": "USDT",
                    "locked": "0",
                    "available": "23.123",
                    "crossedMaxAvailable": "23.123",
                    "isolatedMaxAvailable": "23.123",
                    "maxTransferOut": "23.123",
                    "accountEquity": "23.123",
                    "usdtEquity": "23.123",
                    "btcEquity": "0.001403612744",
                    "unrealizedPL": "0",
                    "coupon": ""
                }
            ]
        },
        {
            "userId": 1234567890,
            "assetList": [
                {
                    "marginCoin": "USDT",
                    "locked": "0",
                    "available": "11",
                    "crossedMaxAvailable": "11",
                    "isolatedMaxAvailable": "11",
                    "maxTransferOut": "11",
                    "accountEquity": "11",
                    "usdtEquity": "11",
                    "btcEquity": "0.000667722189",
                    "unrealizedPL": "0",
                    "coupon": ""
                }
            ]
        }
    ],
    "msg": "success",
    "requestTime": 1630901215622
}
```
