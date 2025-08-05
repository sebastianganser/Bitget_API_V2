---
conversion_date: "2025-03-12"
document_title: "Demo Trading | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/demotrading/websocket"
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
- Use the Demo API Key to start trading.

## WebSocket

Please use the created Demo API Key for WebSocket connections and request the demo trading service address:

- **Public:** `wss://wspap.bitget.com/v2/ws/public`
- **Private:** `wss://wspap.bitget.com/v2/ws/private`

## Websocket Demo Coin Trading

Bitget websocket also supports the demo coin trading, please use a real trading API key to make calls for demo symbol.

- **Public channel:** `wss://ws.bitget.com/v2/ws/public`
- **Private channel:** `wss://ws.bitget.com/v2/ws/private`

## Tickers Channel

In websocket subscribe, simply use the demo symbol and demo coin if any.

### Request Example
```json
{
  "op":"subscribe",
  "args":[
    {
        "instType": "SUSDT-FUTURES",
        "channel": "ticker",
        "instId": "SBTCSUSDT"
    }
  ]
}
```

### Successful Response Example
```json
{
  "event":"subscribe",
  "arg":{
        "instType": "SUSDT-FUTURES",
        "channel": "ticker",
        "instId": "SBTCSUSDT"
  }
}
```

### Push Data Example
```json
{
    "action": "snapshot",
    "arg": {
        "instType": "SUSDT-FUTURES",
        "channel": "ticker",
        "instId": "SBTCSUSDT"
    },
    "data": [
        {
            "instId": "SBTCSUSDT",
            "last": "27000.5",
            "bidPr": "27000",
            "askPr": "27000.5",
            "bidSz": "2.71",
            "askSz": "8.76",
            "open24h": "27000.5",
            "high24h": "30668.5",
            "low24h": "26999.0",
            "priceChangePercent": "-0.00002",
            "fundingRate": "0.000010",
            "nextFundingTime": 1695722400000,
            "markPrice": "27000.0",
            "indexPrice": "25702.4",
            "quantity": "929.502",
            "baseVolume": "368.900",
            "quoteVolume": "10152429.961",
            "openUtc": "27000.5",
            "symbolType": 1,
            "symbol": "SBTCSUSDT",
            "deliveryPrice": "0",
            "ts": 1695715383021
        }
    ],
    "ts": 1695715383039
}
```

