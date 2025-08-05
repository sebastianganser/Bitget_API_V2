---
conversion_date: "2025-03-12"
document_title: "Get Merchant Information | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/p2p/Get-Merchant-Information"
---

# Get Merchant Information | Bitget API

## Get Merchant Information

**Frequency limit:** 10 times/1s (UID)

### Description
Get Merchant Information

### HTTP Request
```
GET /api/v2/p2p/merchantInfo
```

### Request Parameters
N/A

### Request Example
```bash
curl "https://api.bitget.com/api/v2/p2p/merchantInfo" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameter
| Parameter              | Type    | Description                             |
|------------------------|---------|-----------------------------------------|
| registerTime           | String  | Registration time                       |
| nickName               | String  | Alias                                   |
| merchantId             | String  | Merchant ID                             |
| kycStatus              | Boolean | KYC or not <br>true: yes<br>false: no  |
| emailBindStatus        | Boolean | Email bound? <br>true: yes<br>false: no|
| mobileBindStatus       | Boolean | Phone number bound? <br>true: yes<br>false: no|
| email                  | String  | Email                                   |
| mobile                 | String  | Phone number                            |
| avgPaymentTime         | String  | Average payment time in minutes         |
| avgReleaseTime         | String  | Average coin release time in minutes    |
| totalTrades            | String  | Total traded orders                     |
| totalBuy               | String  | Total number of purchase orders         |
| totalSell              | String  | Total number of sell orders             |
| totalCompletionRate    | String  | Total execution rate                    |
| trades30d              | String  | 30-day trading volume                   |
| sell30d                | String  | 30-day sell orders                      |
| buy30d                 | String  | 30-day purchase orders                  |
| completionRate30d      | String  | 30-day close rate                       |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1681194805204,
    "data": {
        "registerTime": "1672039640000",
        "nickName": "lz",
        "merchantId": "1",
        "avgPaymentTime": "172695",
        "avgReleaseTime": "33009",
        "totalTrades": "2",
        "totalBuy": "1",
        "totalSell": "0",
        "totalCompletionRate": "1",
        "trades30d": "12",
        "sell30d": "4",
        "buy30d": "8",
        "completionRate30d": "0.71",
        "kycStatus": true,
        "emailBindStatus": true,
        "mobileBindStatus": true,
        "email": "******@*****.com",
        "mobile": "18*34"
    }
}
```

