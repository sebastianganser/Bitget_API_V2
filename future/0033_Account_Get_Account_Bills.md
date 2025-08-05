---
conversion_date: "2025-03-19"
document_title: "Get Account Bills | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Get-Account-Bill"
---

# Get Account Bills | Bitget API

**Rate limit:** 10 req/sec/UID

## Description
Get Account bills (It only supports to get the data within 90 days. The older data can be downloaded from web)

## HTTP Request
```
GET /api/v2/mix/account/bill
```

## Request Parameters
| Parameter       | Type   | Required | Description |
|----------------|--------|----------|-------------|
| productType    | String | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| coin           | String | No       | Currency<br>It's valid only when the businessType is "trans_from_exchange" or "trans_to_exchange" |
| businessType   | String | No       | unknown: unknown<br>trans_from_exchange: transfer in from SPOT account<br>trans_to_exchange: transfer out to SPOT account<br>open_long: open long<br>open_short: open short<br>close_long: close long<br>close_short: close short<br>force_close_long: force close long (when burst)<br>force_close_short: force close short (when burst)<br>contract_settle_fee: funding fee<br>append_margin: adjust margin<br>adjust_down_lever_append_margin: reduce leverage add margin<br>reduce_margin: reduce margin<br>auto_append_margin: automatic margin call<br>cash_gift_issue: distribute coupon/gift/card<br>cash_gift_recycle: recycling coupon/gift/card<br>tracking_follow_pay: follower tracking order pay<br>tracking_follow_back: follower tracking order cashback<br>tracking_trader_income: tracking order income<br>burst_long_loss_query: burst close long<br>burst_short_loss_query: burst close short<br>trans_from_contract: transfer in from FUTURE account<br>trans_to_contract: transfer out to FUTURE account<br>trans_from_otc: transfer in from OCT account<br>trans_to_otc: transfer out to OCT account<br>buy: buy in one_way_mode<br>sell: sell in one_way_mode<br>force_buy: force buy in one_way_mode<br>force_sell: force sell in one_way_mode<br>burst_buy: burst buy<br>burst_sell: burst sell<br>bonus_issue: bonus/coupon issue<br>bonus_recycle: bonus/coupon recycle<br>bonus_expired: bonus/coupon expired<br>delivery_long: delivery future settle long<br>delivery_short: delivery future settle short<br>trans_from_cross: transfer in from CROSS account<br>trans_to_cross: transfer out to CROSS account<br>trans_from_isolated: transfer in from ISOLATED account<br>trans_to_isolated: transfer out to ISOLATED account |
| onlyFunding    | String | No       | The following four types of non-financial businessType will be excluded.<br>default: no<br>yes: excluded<br>no: included<br>The following four businessType:<br>append_margin, adjust_down_lever_append_margin, reduce_margin, auto_append_margin |
| idLessThan     | String | No       | Requests the content on the page before this ID (older data), the value input should be the endId of the corresponding interface. |
| startTime      | String | No       | Start time, ms<br>The interval between the startTime and the endTime should be <= 30 days |
| endTime        | String | No       | End time, ms<br>The interval between the startTime and the endTime should be <= 30 days |
| limit          | String | No       | Page size, max 100, default 20 |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/account/bill?productType=USDT-FUTURES" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters
| Parameter | Type | Description |
|-----------|------|-------------|
| bills     | Array | Bill list |
| endId     | String | The final transaction order ID.<br>This is used when idLessThan/idGreaterThan is set as a range. |

### Bill Fields
| Parameter         | Type   | Description |
|------------------|--------|-------------|
| billId           | String | Bill ID |
| symbol           | String | Symbol |
| amount           | String | Amount |
| fee              | String | Fee |
| feeByCoupon      | String | Fee paid by the coupon |
| businessType     | String | Business Type (same list as above) |
| coin             | String | Coin: USDT |
| balance          | String | Balance |
| cTime            | String | Created Time, ms |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695809161807,
    "data": {
        "bills": [
            {
                "billId": "1",
                "symbol": "BTCUSDT",
                "amount": "-0.004992",
                "fee": "0",
                "feeByCoupon": "",
                "businessType": "contract_settle_fee",
                "coin": "USDT",
                "balance": "232.21",
                "cTime": "1695715200654"
            },
            {
                "billId": "2",
                "symbol": "ETHUSDT",
                "amount": "0",
                "fee": "-0.222012",
                "feeByCoupon": "",
                "businessType": "open_long",
                "coin": "USDT",
                "balance": "232.21",
                "cTime": "1695714563516"
            }
        ],
        "endId": "2"
    }
}
```

