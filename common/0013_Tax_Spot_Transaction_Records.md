---
conversion_date: "2025-03-11"
document_title: "Spot Transaction Records | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/tax/Get-Spot-Account-Record"
---

# Spot Transaction Records | Bitget API

## Spot Transaction Records

**Frequency limit:** 1 times/1s (User ID)

### Description
Spot transaction records

### HTTP Request
```
GET /api/v2/tax/spot-record
```

### Request Parameters
| Parameter    | Type   | Required | Description                                      |
|--------------|--------|----------|--------------------------------------------------|
| coin         | String | No       | Default all coin type                           |
| startTime    | String | Yes      | Start time, Unix millisecond timestamps         |
| endTime      | String | Yes      | End time, Unix millisecond timestamps           |
|              |        |          | The maximum interval between startTime and endTime is 30 days. |
| limit        | String | No       | Default: 500, maximum: 500                      |
| idLessThan   | String | No       | The last recorded ID                            |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/tax/spot-record?startTime=16861" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameters
| Parameter      | Type   | Description                          |
|----------------|--------|--------------------------------------|
| id             | String | Record ID                            |
| coin           | String | Coin                                 |
| spotTaxType    | String | tax type spot                        |
| amount         | String | Quantity                             |
| fee            | String | Transaction fee                      |
| balance        | String | Total accounts                       |
| ts             | String | When this record was generated Timestamp |

### spotTaxType
- Deposit
- Withdrawal
- User fees
- Fiat withdrawal success - Deduct
- Sell
- Buy
- Transaction fee deduct
- Strategic purchase-user accounts
- Subscribe to trader-user accounts
- System charges fees
- Strategic refund-User account
- Subscription fee refund-user account
- Strategic Income-Traders' accounts
- Crypto Voucher Distribution
- Copy Trade expense
- Judicial recall
- Copy Trade profit
- Refund Copy Trade commission
- Buy Crypto
- Deduction of judicial recall
- Buy with card
- Airdrop Reward-B
- Decrease due to ETF settlement
- Increase due to ETF settlement
- System lock-up
- User lock-up
- Trading fee rebate
- Manage background lock positions
- Automatic deposit
- Automatic withdrawal
- Deposit from strategy account
- Withdraw to strategy account
- Lotto rewards
- User contract trial fund
- User contract simulation fund
- Delegate
- Undelegate
- Rebate rewards
- Consumption
- Gains
- Unlock locked order
- Deduction
- Return
- Release
- Repayment
- Forced liquidation return
- The locked order is returned to the system
- Failed
- Withdrawal frozen
- Mirror fund
- Supplement fund
- Reduce fund
- Settlement out
- Withdrawal unfreeze
- Ordinary Withdrawal
- Fast withdrawal fee
- Airdrop Reward-A
- Subscribe
- Interest
- Penalty
- Redemption
- Activity fund(USDT-Ⓜ)
- Activity fund
- Activity fund(Coin-Ⓜ)
- Increase exchange rate
- Reduce exchange rate
- Transfer in
- Activity issuance
- Transfer out
- Super account
- Exchange spending
- Exchange income
- Sent
- Received
- MegaSwap Transfer in
- MegaSwap Transfer out
- Channel referral rewards
- System account
- Sell Crypto
- Fiat deposit

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1687257612262,
    "data": [
        {
            "id": "1",
            "coin": "AIBB",
            "spotTaxType": "Interest",
            "amount": "6018333.33333333",
            "fee": "0",
            "balance": "468575833.33333306",
            "ts": "1686128884851"
        }
    ]
}
```
