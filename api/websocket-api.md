# Websocket API

{% hint style="info" %}
This section is under construction
{% endhint %}

## Websocket Endpoint

To access the AMP websocket, connect to the following endpoint: 

```javascript
https://amp.exchange/api/socket
```

## Orders

### **New Order Message**

**Example New Order Message:**

```javascript
{
    "channel":"orders",
    "event":{
        "type":"NEW_ORDER",
        "hash":"0xee402593792f88c86c7abb9caa8847705b3d1b4ea33b23d99b5f8cb37556658d",
        "payload":{
            "exchangeAddress":"0x9c446449fbc378941586Ef7a2196B13CC12AEBcd",
            "userAddress":"0xfA4f991cAA4f37f7bCE2e285e155da8C929658eF",
            "baseToken":"0x136c4443c3980c3db40ff79ef7efc2ea4b1ff062",
            "quoteToken":"0x84e7c51c50143a19aa7e6895b7642f30262b6894",
            "amount":"100000000000000000",
            "pricepoint":"100000000000000000000000000",
            "side":"SELL",
            "makeFee":"500000",
            "takeFee":"500000",
            "nonce":"7552999023283224",
            "hash":"0xee402593792f88c86c7abb9caa8847705b3d1b4ea33b23d99b5f8cb37556658d",
            "signature":{
                "R":"0x0429446917dc2779ba2f7d8d63d8164d1b3c60e35e11c3116613f2976fdd74c3",
                "S":"0x1862a129a377d19b9ab35517dc549bbab050af60b9263194b9c79797b67603af",
                "V":28
            }
        }
    }
}
```

**Example Response Message:**

```javascript
{
    "channel": "orders",
    "event": {
        "type": "ORDER_ADDED",
        "hash": "0x",
        "payload": {

            "exchangeAddress": "0x9c446449fbc378941586ef7a2196b13cc12aebcd",        
            "userAddress": "0xfa4f991caa4f37f7bce2e285e155da8c929658ef",
            "pairName": "WETH/USDC"
            "quoteToken": "0x84e7c51c50143a19aa7e6895b7642f30262b6894"            
            "baseToken": "0x136c4443c3980c3db40ff79ef7efc2ea4b1ff062",
            "side": "SELL",
            "status": "OPEN",
            "pricepoint": "100000000000000000000000000",
            "amount": "100000000000000000",
            "filledAmount": "0",
            "hash": "0xee402593792f88c86c7abb9caa8847705b3d1b4ea33b23d99b5f8cb37556658d"
            "takeFee": "500000",
            "makeFee": "500000",
            "nonce": "7552999023283224",
            "signature": {
                R: "0x0429446917dc2779ba2f7d8d63d8164d1b3c60e35e11c3116613f2976fdd74c3", 
                S: "0x1862a129a377d19b9ab35517dc549bbab050af60b9263194b9c79797b67603af", 
                V: 28
            },
            "createdAt": "2019-02-09T20:27:21.331894+09:00",
        }
    }
}

```

### Cancel Order Message

**Example Cancel Order Message:**

```javascript
{
    "channel":"orders",
    "event":{
        "type":"CANCEL_ORDER",
        "hash":"0x0de2a60193ba5608024c561a65684dae6cb1d401ef1205d7e2fd8d7b044f3343",
        "payload":{
            "orderHash":"0x65a79d58791113c170ff65f542644f599cd29b4946eb599d7f4bcc0a0dce20d9",
            "hash":"0x0de2a60193ba5608024c561a65684dae6cb1d401ef1205d7e2fd8d7b044f3343",
            "signature":{
                "R":"0x6a0555b7241040ea04d48dd55ebcb1bf69f5fb4d771b29f68f8de125c102c543",
                "S":"0x394d0972291a93bf458c0bf9972f09dadca3b20c4e97058437331942942a45a4",
                "V":27
            }
        }
    }
}
```

**Example Response Message:** 

```javascript
{
    "channel": "orders",
    "event": {
        "type": "ORDER_CANCEL",
        "hash": ,
        "payload": {
            "amount": "100000000000000000"
            "baseToken": "0x136c4443c3980c3db40ff79ef7efc2ea4b1ff062"
            "createdAt": "2019-02-08T07:36:39.108Z"
            "exchangeAddress": "0x9c446449fbc378941586ef7a2196b13cc12aebcd"
            "filledAmount": "0"
            "hash": "0x65a79d58791113c170ff65f542644f599cd29b4946eb599d7f4bcc0a0dce20d9"
            "makeFee": "500000"
            "nonce": "7213737708513919"
            "pairName": "WETH/USDC"
            "pricepoint": "200000000000000000000000000"
            "quoteToken": "0x84e7c51c50143a19aa7e6895b7642f30262b6894"
            "side": "SELL"
            "signature": {
                R: "0x26f08b43a799fbb7bb5163f040b81aa54d718f15df069ae6e114659f4dbc2c3d", 
                S: "0x3f18aed7ce51cc8a284ca8552255bfa26a75f1c8d3c0706e4851b96ceef3822f", 
                V: 28
            },
            "status": "CANCELLED"
            "takeFee": "500000"
            "userAddress": "0xfa4f991caa4f37f7bce2e285e155da8c929658ef"
        }
    }
}
```

## OHLCV

### **Subscribe Message**

```javascript
{
    "channel":"ohlcv",
    "event":{
        "type":"SUBSCRIBE",
        "payload":{
            "name":"WETH/USDC",
            "baseToken":"0x136c4443c3980c3db40ff79ef7efc2ea4b1ff062",
            "quoteToken":"0x84e7c51c50143a19aa7e6895b7642f30262b6894",
            "from":1518596695,
            "to":1549700695,
            "duration":1,
            "units":"hour",
        }
    }
}
```

### **Unsuscribe Message**

```javascript
{
    "channel":"ohlcv",
    "event": {
        "type":"UNSUBSCRIBE"
    }
}
```

## Order Book

### **Subscribe Message**

```javascript
{
    "channel":"orderbook",
    "event": {
        "type":"SUBSCRIBE",
        "payload":{
            "name":"WETH/USDC",
            "baseToken":"0x136c4443c3980c3db40ff79ef7efc2ea4b1ff062",
            "quoteToken":"0x84e7c51c50143a19aa7e6895b7642f30262b6894"
        }
    }
}
```

### **Unsubscribe Message**

```javascript
{
    "channel":"orderbook",
    "event": {
        "type":"UNSUBSCRIBE"
    }
}
```

## Trades

### **Subscribe Message**

```javascript
{
    "channel":"trades",
    "event": {
        "type":"SUBSCRIBE",
        "payload": {
             "name":"WETH/USDC",
             "baseToken":"0x136c4443c3980c3db40ff79ef7efc2ea4b1ff062",
             "quoteToken":"0x84e7c51c50143a19aa7e6895b7642f30262b6894"
         }
     }
 }
```

### **Unsubscribe Message**

```javascript
{
    "channel":"trades",
    "event": {
        "type":"UNSUBSCRIBE"
    }
}
```

\*\*\*\*



