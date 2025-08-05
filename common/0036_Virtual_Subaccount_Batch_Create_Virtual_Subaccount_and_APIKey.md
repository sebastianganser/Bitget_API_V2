---
conversion_date: "2025-03-12"
document_title: "Batch Create Virtual Subaccount and Apikey | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Batch-Create-Virtual-Subaccount-And-Apikey"
---

# Batch Create Virtual Subaccount and Apikey

**Frequency limit:** 1 times/1s (User ID)

## Description
Create the virtual sub-account and apikey in batch.

- The max length of list is 5 in each request.
- Every sub-account can create up to 10 API Key.
- You can create up to 20 sub-accounts.

## HTTP Request
```
POST /api/v2/user/batch-create-subaccount-and-apikey
```

## Request Parameters
| Parameter       | Type   | Required | Description                                                                 |
|----------------|--------|----------|-----------------------------------------------------------------------------|
| subAccountName | String | Yes      | Virtual sub-account alias, 8-character English letters                      |
| passphrase     | String | Yes      | Passcode, English letters of 8−32 characters + numbers                     |
| label          | String | Yes      | Sub-account note, Length 20                                                |
| ipList         | List   | No       | Virtual sub-account ApiKey IP whitelist, Max. 30                           |
| permList       | List   | No       | Sub-account permissions: 
  - spot_trade: Spot trade
  - margin_trade: Spot Margin trade
  - contract_trade: Futures trade read-write
  - read: Read permissions |

## Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/user/batch-create-subaccount-and-apikey" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \  
   -d '[{"subAccountName":"test","passphrase":"12345678","permList":["spot_trade","margin_trade","contract_trade"],"label":"1681808312065"}]'
```

## Response Parameters
| Parameter         | Type   | Description                                                  |
|------------------|--------|--------------------------------------------------------------|
| subAccountUid     | String | Virtual sub-account UID                                      |
| subAccountName    | String | Virtual sub-account alias, 8-character English letters        |
| label             | String | Sub-account note, Length 20                                   |
| subAccountApiKey  | String | Sub-account API key                                          |
| secretKey         | String | Sub-account secret key                                       |
| permList          | List   | Sub-account permissions:
  - spot_trade: Spot trade
  - margin_trade: Spot Margin trade
  - contract_trade: Futures trade read-write
  - read: Read permissions |
| ipList            | List   | IP whitelist                                                 |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1682662465346,
    "data": [
        {
            "subAccountUid": "***********",
            "subAccountName": "*****@*******.com",
            "label": "1681808312065",
            "subAccountApiKey": "xx_xxx",
            "secretKey": "XXXXXXXXXXXXXXX",
            "permList": [
                "spot_trade",
                "margin_trade",
                "contract_trade"
            ],
            "ipList": [
                "127.0.0.1"
            ]
        }
    ]
}
```
