---
conversion_date: "2025-03-11"
document_title: "RSA Signature Sample | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/signature-samaple/rsa"
---

# RSA | Bitget API

## RSA Signature Demo Code

### Python
```python
import base64
import json
import time
import base64
from Crypto.Hash import SHA256
from Crypto.Signature import PKCS1_v1_5
from Crypto.PublicKey import RSA

def get_timestamp():
    return int(time.time() * 1000)

def rsa_sign(message, private_key):
    pri_key = RSA.importKey(private_key)
    encoded_param = SHA256.new(bytes(message, encoding='utf-8'))
    sign_str = PKCS1_v1_5.new(pri_key).sign(encoded_param)
    return base64.b64encode(sign_str).decode()

def pre_hash(timestamp, method, request_path, body):
    return str(timestamp) + str.upper(method) + request_path + body

def parse_params_to_str(params):
    params = [(key, val) for key, val in params.items()]
    params.sort(key=lambda x: x[0])
    from urllib.parse import urlencode
    url = '?' + urlencode(params)
    if url == '?':
        return ''
    return url

if __name__ == '__main__':
    private_key = '''-----BEGIN PRIVATE KEY-----
XXXXXXXXXXANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCdTR5gmwGH77wE
xxxxxxxxxxiw7fPXWhMh7gZwurQQ8M/I9/VA8lDjwwoGuuJ6enurdfwhpZxeZH
xxxxxxxxxxSEXVuxJv5hdpI9m6ydInK9SA8IbaF4yYWp0l4N2mA44MzadA7QZq
xxxxxxxxxxa5q/NZHFWCrCbW2lGAAWwrhQq9LceVIW75e213xtnps0pGlII7Ye
xxxxxxxxxxYNSxlCdLOiz1GvOeVSeiSZx31o/O+rj7tDFpSgZJEXRmtGRoJkJy
xxxxxxxxxxVSOcb1hCExg4osK6rBKnDjFjwQvwvNNZq0JG+CkfH8eHAa7gSK50
xxxxxxxxxxAAECggEAEvYk30hQGu7PH0stQX3UhlVsR6HXnRlvgIrmJe7F/VLO
xxxxxxxxxx/heYY1nsX8+mIyjmvEOayqPgdkEmXevVlcuQf38Zbduynr3vlRCX
xxxxxxxxxxSxFBODuu/EAZc3mm27C2wUV7w6SAy9g0g6Os97ehZsSGAwHl4aye
xxxxxxxxxxEh5Ptq4YAfCYiUO7j10pQ+DJKqN9N1eyjyw5eixEgCpudcbpCc9X
xxxxxxxxxxANX8/LwvokqgYBK1UIL6ear0dtKmeFU+KwrmkKZfXk8/Amr/O8Ot
xxxxxxxxxxzq3La149LMmNkUYxaMSV/KGTEV7ukQKBgQDQl/fA3mxXtQg2IjTB
xxxxxxxxxxECWcP7TQWJDb30vxOKeq1k9YPUfegZga5zlyV28PAZnb0m5x07+0
xxxxxxxxxxe9OhQxfkAY6AtJaiIqhCcw5ew8Go/Ja1ML0jZESWG1MWBJtCcFTm
xxxxxxxxxxe0adilYmyu7zwwKBgQDBDPJZgSj7YssPyRmo3bO0MjknfYBqXvwi
xxxxxxxxxxJ9Rc2WXGfEm3DEn7TO/Wv0t7Yqm6/sXg5HzriN/PHlaVtE6wlXe7
xxxxxxxxxx7KKWYqP812mASl6ydLX9QWozlOXjVhWMuSGqMWjut4J3P8jlkOJ6
xxxxxxxxxxgQCxwvAl8ubNj78hsuDWgsddKIMkwvKrfdsvXrMOYouAdLjZJvjs
xxxxxxxxxxs9km8g/479pYlOn+Iv/Z7Lqke8/HdOFASoQ9h1nSuujgEgXUwkg1
xxxxxxxxxx2BY3FPnGGh8iQma1pdkUVn35fAq/m7e/S+kP1JY6lPIx1QKBgQCS
xxxxxxxxxxpot+ceGt2bseSd8l4jqU3nDZ0oW8+4Qnnu9QFhN4Hn9wIjpAOGaU
xxxxxxxxxxVbior98JxMSDHsHmuXKPA8DishumGlqV+vxsIzLQD1Ge/dbqsERB
xxxxxxxxxxiyUNqjk5kcPQeHIyJk5qQaF21udoTQKBgDOMbtM0Nq7cd/SAHISR
xxxxxxxxxxLJW7DRJGxw3AEwxKG+nxNLeG7GsQDyPCvZSKwRpdpXRTh+6mzXqe
xxxxxxxxxxz8Cwo6tgyKRi6QPObQk00vbrKEBTihP30m81rwBPzjwj7iKXxWgA
DJoVsaqGOaIf4qXXXXXXXXXX
-----END PRIVATE KEY-----'''
    
    timestamp = get_timestamp()
    request_path = "/api/v2/mix/order/place-order"
    
    # POST
    params = {
        "symbol": "TRXUSDT",
        "marginCoin": "USDT",
        "price": 0.0555,
        "size": 551,
        "side": "buy",
        "orderType": "limit",
        "force": "normal"
    }
    body = json.dumps(params)
    sign = rsa_sign(pre_hash(timestamp, "POST", request_path, str(body)), private_key)
    print(sign)

    # GET
    body = ""
    request_path = "/api/v2/mix/account/account"
    params = {"symbol": "TRXUSDT", "marginCoin": "USDT"}
    request_path = request_path + parse_params_to_str(params)  # Need to be sorted in ascending alphabetical order by key
    sign = rsa_sign(pre_hash(timestamp, "GET", request_path, str(body)), private_key)
    print(sign)
```

