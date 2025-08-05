---
conversion_date: "2025-03-11"
document_title: "Websocket API | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/websocket-intro"
  - "https://www.bitget.com/api-doc/common/public/Get-Server-Time"
  - "https://www.bitget.com/api-doc/common/signature-samaple/rsa"
---

# Websocket API

## Overview

WebSocket is a new HTML5 protocol that achieves full-duplex data transmission between the client and server, allowing data to be transferred effectively in both directions. A connection between the client and server can be established with just one handshake. The server will then be able to push data to the client according to preset rules. Its advantages include:

- The WebSocket request header size for data transmission between client and server is only 2 bytes.
- Either the client or server can initiate data transmission.
- There's no need to repeatedly create and delete TCP connections, saving resources on bandwidth and server.

It is strongly recommended that developers use WebSocket API to obtain market information and transaction depth.

| Domain | WebSocket API | Recommended to use |
|--------|----------------|--------------------|
| Websocket Domain | `wss://ws.bitget.com/v2/ws/public` | Main Domain, Public channel |
| Websocket Domain | `wss://ws.bitget.com/v2/ws/private` | Main Domain, Private channel |

## Connect

### Connection instructions:

- Connection limit: 300 connection requests/IP/5min, Max 100 connections/IP
- Subscription limit: 240 subscription requests/Hour/connection, Max 1000 channel subscription/connection
- If there’s a network problem, the system will automatically disconnect the connection.

To keep the connection stable:
- Websocket will be forcibly disconnected every 24 hours, please add the reconnection mechanism in your code
- Users set a 30 seconds timer to send string "ping", and expect a string "pong" as response. If no string "pong" received, please reconnect
- Websocket server will disconnect the connection if there is no string "ping" received for 2 min
- The Websocket server accepts up to 10 messages per second. The message includes:
  - String "ping"
  - JSON message, such as subscribe, unsubscribe
- If the user sends more messages than the limit, the connection will be disconnected. The IP which is repeatedly disconnected may be blocked by the server
- We highly recommend you to subscribe less than 50 channels in one connection. The connections with less channel subscriptions will be more stable.

## Login

- `apiKey`: Unique identification for invoking API. Requires user to apply one manually.
- `passphrase`: APIKey password
- `timestamp`: the Unix Epoch time, the unit is seconds (**different from the signature timestamp of restAPI**)
- `secretKey`: The security key generated when the user applies for APIKey, e.g.: `22582BD0CFF14C41EDBF1AB98506286D`

### Example of timestamp

### Sign

- `method`: always 'GET'.
- `requestPath`: always `/user/verify`
- `sign`: signature string, the signature algorithm is as follows:
  - First concatenate `timestamp`, `method`, `requestPath`, then use HMAC SHA256 method to encrypt the concatenated string with SecretKey, and then perform Base64 encoding.
  - The request will expire 30 seconds after the timestamp. If your server time differs from the API server time, we recommended using the REST API to query the [API server time](https://www.bitget.com/api-doc/common/public/Get-Server-Time) and then compare the timestamp.

### Steps to generate the final signature

**HMAC**
- Step 1. concat the content
- Step 2. Use the private key `secretkey` to encrypt the string to be signed with hmac sha256
- Step 3. The final step is to base64 encode the hash

**RSA**
- Step 1. Use the RSA `privateKey` to encrypt the string to be signed with SHA-256
- Step 2. Base64 encoding for Signature

> If login fails, it will automatically disconnect

### Request Format Description
```javascript
const timestamp ='' + Date.now() / 1000
sign=CryptoJS.enc.Base64.Stringify(CryptoJS.HmacSHA256(timestamp +'GET'+'/user/verify', secretKey))
```
```java
Long timestamp = System.currentTimeMillis() / 1000;
String content = timestamp +"GET"+"/user/verify";
String hash = hmac_sha256(content, secretkey);
String sign = base64.encode(hash);
```

## Request Example
```json
{
  "op":"login",
  "args":[
    {
      "apiKey":"<api_key>",
      "passphrase":"<passphrase>",
      "timestamp":"<timestamp>",
      "sign":"<sign>"
    }
  ]
}
```
```json
{
  "op":"login",
  "args":[
    {
      "apiKey":"xx_xxx",
      "passphrase":"xxx",
      "timestamp":"1538054050",
      "sign":"8RCOqCJAhhEh4PWcZB/96QojLDqMAg4qNynIixFzS3E="
    }
  ]
}
```
### Successful Response Example
```json
{
  "event":"login",
  "code":"0",
  "msg":""
}
```
### Failure Response Example
```json
{
  "event":"error",
  "code":"30005",
  "msg":"error"
}
```

... (truncated for brevity)
