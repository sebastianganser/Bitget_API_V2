---
conversion_date: "2025-03-12"
document_title: "Futures Trading API | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/intro"
  - "https://www.bitget.com/api-doc/common/demotrading/restapi"
  - "https://www.bitget.com/api-doc/contract/account/Get-Account-List"
---

# Futures Trading API | Bitget API

## Futures Trading API

This section introduces the API documentation for Futures trading.

For more details, please refer to the menu on the left.

Please note that there are 3 product types under Futures trading for RestAPI and Websocket:

| Product Type     | Desc                                      |
|------------------|-------------------------------------------|
| USDT-FUTURES     | USDT-M Futures, Futures settled in USDT   |
| COIN-FUTURES     | USDC-M Futures, Futures settled in USDC   |
| USDC-FUTURES     | Coin-M Futures, Futures settled in cryptocurrencies |

Specially, these are the product type value for **demo trading** in RestAPI and Websocket:

| Product Type      | Desc                                             |
|-------------------|--------------------------------------------------|
| SUSDT-FUTURES     | USDT-M Futures Demo (Try out USDT-M futures trading) |
| SCOIN-FUTURES     | Coin-M Futures Demo (Try out Coin-M futures trading) |
| SUSDC-FUTURES     | USDC-M Futures Demo (Try out USDC-M futures)        |

Every account has certain demo coins, you could check your demo coin balance by calling the **Account List API** with above demo trading product type.

[Account List API](https://www.bitget.com/api-doc/contract/account/Get-Account-List)
