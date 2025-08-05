---
conversion_date: "2025-03-12"
document_title: "Demo Trading | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/demotrading/restapi"
---

# Demo Trading | Bitget API

## Demo Trading

Demo trading allows you to practice trading and test strategies in a real-market environment using virtual funds, helping you improve your skills and reduce the risk of losses. KYC is needed.

## API Key

To perform demo trading via API, you'll need to create a Demo API Key in the first place. The steps are as follows:

- Log in to your account
- Switch to Demo mode
- Go to the Personal Center
- Go to the API Key Management
- Create a Demo API Key
- Use the Demo API Key to start trading

## REST

Please use the created Demo API Key for API calls, and add `paptrading` in the request header, with the value set to `1`.

## RestAPI Demo Coin

We suggest users to use demo coin trading.

### Demo Coin Testing

Demo coins include: `SUSDT`, `SBTC`, `SETH`, `SEOS`, `SUSDC`. Demo coin does not have actual value; it is only for users to do the simulated trading. Demo coin will be in your account after account registration: **Futures Account - USDT_M Futures Demo**

Demo symbol name pattern is: `SBTCSUSDT`

Please use a real trading API key to make calls for demo symbol.

Simulated trading does not support to use sub-account in most of interfaces, please use main account.

## Get Demo Trading Symbol Config

### Request Sample

- **Method:** `GET`
- **productType**
  - `susdt-futures` – USDT simulation perpetual contract
  - `scoin-futures` – Universal margin simulation perpetual contract
  - `susdc-futures` – USDC simulation perpetual contract

### Response Body

As we can see from the example, values of symbol and coin are demo symbol/demo coin.

Demo symbol and demo coin must be shown in pairs, a wrong pair will result to an interface error.

### Future Place Order Demo Trading

```bash
curl "https://api.bitget.com/api/v2/mix/market/contracts?productType=susdt-futures"
```

```json
{
    "code": "00000",
    "data": [
        {
            "baseCoin": "SBTC",
            "buyLimitPriceRatio": "0.01",
            "feeRateUpRatio": "0.005",
            "limitOpenTime": "-1",
            "maintainTime": "",
            "makerFeeRate": "0.0002",
            "minTradeNum": "0.001",
            "offTime": "-1",
            "openCostUpRatio": "0.01",
            "priceEndStep": "5",
            "pricePlace": "1",
            "quoteCoin": "SUSDT",
            "sellLimitPriceRatio": "0.01",
            "sizeMultiplier": "0.001",
            "supportMarginCoins": [
                "SUSDT"
            ],
            "symbol": "SBTCSUSDT",
            "symbolStatus": "normal",
            "symbolType": "perpetual",
            "takerFeeRate": "0.0006",
            "volumePlace": "3",
            "deliveryTime": "",
            "deliveryStartTime": "",
            "launchTime": "",
            "fundInterval": "",
            "minLever": "",
            "maxLever": "",
            "posLimit": ""
        }
    ],
    "msg": "success",
    "requestTime": 1690313813709
}
```

## Request Sample

- **Request URI**: `/api/v2/mix/order/place-order`
- **Method**: `POST`

A demo trade order ID will be returned when input parameter `symbol` and `marginCoin` are demo symbol/demo coin.

### Response Body

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/place-order" \
-H "ACCESS-KEY:*******" \
-H "ACCESS-SIGN:*******" \
-H "ACCESS-PASSPHRASE:*****" \
-H "ACCESS-TIMESTAMP:1659076670000" \
-H "locale:en-US" \
-H "Content-Type: application/json" \
-d '{
    "symbol": "SETHSUSDT",
    "productType": "susdt-futures",
    "marginMode": "isolated",
    "marginCoin": "SUSDT",
    "size": "1.5",
    "price": "2000",
    "side": "buy",
    "tradeSide": "open",
    "orderType": "limit",
    "force": "gtc",
    "clientOid": "12121212122",
    "reduceOnly": "NO",
    "presetStopSurplusPrice": "2300",
    "presetStopLossPrice": "1800"
}'
```

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1627293504612,
    "data": {
        "orderId": "121211212122",
        "clientOid": "121211212122"
    }
}
```
