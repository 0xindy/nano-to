![line](https://github.com/fwd/n2/raw/master/.github/line.png)

<h1 align="center">Nano Name Service</h1>
<h3 align="center">Hosted on Github</h3>

![line](https://github.com/fwd/n2/raw/master/.github/line.png)

<p align="center">
  <img src="https://github.com/fwd/nano/raw/master/dist/images/banner.png" alt="Nano.to" />
</p>

![line](https://github.com/fwd/n2/raw/master/.github/line.png)

## Quick Links

- **Nano.to (Github)**
  - [Checkout Pages](#checkout-pages)
  - [Customize Checkout](#checkout-pages)
  - [Register Username](#register-username)
  - [Renew Username](#renew-username)
  - [Username Dataset](#username-dataset)

- **Api.Nano.To**
  - [Checkout POST API](#checkout-api)
  - [Live Fiat Price API](#fiat-price-api)

- **PoW.Nano.To**
  - [Proof of Work API](#gpu-powered-pow-api)

![line](https://github.com/fwd/n2/raw/master/.github/line.png)

## Nano.to Checkout

**Any Address:**
```python
https://nano.to/:ADDRESS
```

**Nano.to Username:**
```python
https://nano.to/@Keeri
```

**Customize Page:**
```python
https://nano.to/@Keeri?amount=50&random=true
```

> Need to provide sensitive information? See [Checkout POST API](#checkout-api)

<img src="https://github.com/fwd/nano/raw/master/dist/images/single-ui.png" alt="Single Panel UI" />

### Checkout with Plans

```python
https://nano.to/@Moon?plans=Tip:0.133,Small:1,Medium:10,Large:20
```

<img src="https://github.com/fwd/nano/raw/master/dist/images/double-ui.png" alt="Single Panel UI" />

## Advanced Example

```python
https://nano.to/@Keeri
?background=$0057b7:$ffd700
&color=$FFF
&highlight=white
&vanity=$0057b7
&qrcode=white:$0057b7
&logo=https://nano.to/dist/logo/cyber.png
```

<img src="https://github.com/fwd/nano/raw/master/dist/images/slava-ui.png" alt="Single Panel UI" />

**Available Params:**

- **amount** (number) : Single panel with price. No plans.
- **plans** (string) : Plans separated by commas. Ex. Tip:30,Small:5
- **currency** (string) : ISO Currency Symbol. Ex JPY
- **image** (image/url) : Display Image. Image URL.
- **random** (boolean) : Use random amounts. Ex + 0.00XXXX
- **color** (string) : Text color. Ex red:blue
- **background** (string) : Background color. Ex white:gray
- **highlight** (string) : Box backgrounds value. Ex blue:red
- **qrcode** (string) : QR Code colors. Ex white:black
- **logo** (image/url) : Replace QR Code logo. Image URL.
- **cancel** (string) : Redirect URL when pressed 'Cancel'
- **success** (string) : Redirect URL on success.

## Checkout API

**Nano.to Checkout UI** is hosted on Github, and can be used without a backend. When you need to use sensitive information like ```webhook_url``` & ```metadata``` send a POST request to ```api.nano.to```. 

```js
const http = require('axios')

http.post('https://api.nano.to', {
  address: '@keeri',
  background: '#0057b7,#ffd700',
  webhook_url: 'https://example.com/secret/endpoint',
  success_url: 'https://example.com/success?hash={{hash}}',
  metadata: { userId: 'joe-mama', password: "Slava Urakini" },
}).then((res) => {
  console.log( res.data )
})
```

**Response**

```json
{
  "id": "f745ffa3",
  "browser": "https://nano.to/id_f745ffa3",
  "json": "https://api.nano.to/checkout/f745ffa3",
  "check": "https://api.nano.to/checkout/f745ffa3/check"
}
```

**Webhook POST Body:**

When payment is confirmed ```api.nano.to``` sends a POST request to the provided URL. 

```json
{
  "id": ":CHECKOUT_ID",
  "block": {
    "hash": ":PAYMENT_HASH",
    "account": ":SENDER_ADDRESS",
    "amount": "10991300000000000000000000000",
    "amount_nano": "0.0109913"
  },
  "plan": {
    "title": "Default",
    "value": "0.0109913",
    "value_raw": "10991300000000000000000000000"
  },
  "metadata": {
    "userId": "joe-mama",
    "password": "Slava Urakini"
  },
  "checkout": "https://api.nano.to/checkout/:CHECKOUT_ID"
}
```

![line](https://github.com/fwd/n2/raw/master/.github/line.png)

## Nano.to Usernames

Registering a Username is easy. Visit [https://nano.to](https://nano.to), and search for your desired username. If available you will see "Username Available". Follow the Checkout UI to complete. 

**Username Renewal**

You can add time to your Username by visting: 

```
https://api.nano.to/:USERNAME/renew
```

You must pay with the address on file. If you wish to change the Address, you must wait for it to expire or contact support@nano.to.

**Grace Period**

Every Username has a 10 day grace period after expiration where only the orignal address may renew it.

## Username Dataset

```pthon
https://nano.to/known.json
```

### Fiat Price API

```pthon
https://api.nano.to/price
```

```json
{
  "price": 5.3012,
  "symbol": "XNO",
  "currency": "USD"
}
```

### GPU Powered PoW API

Standalone, GPU powered proof of work API for the Nano blockchain. Easily scale any Nano application.

```python
https://pow.nano.to/:HASH
```

**or POST request:**
```javascript
axios.post('https://pow.nano.to', { 
    hash: 'HASH'
}).then((res) => {
    // console.log(res.data)
})
```

**Response (JSON):**
```json
{
    "difficulty": "fffffffbc3b93c36",
    "multiplier": "1.888817235874546",
    "work": "157ad78255c73cae",
    "frontier": "277FD6365DF608D601F18F464926B600B15F6CD705A90E2239F55E9F86E7B38F",
    "remaining": 4,
    "cached": false,
    "duration": "0.201s",
    "server": "Nano.to/GPU-4"
}
```

> 5 Free / Minute (\~0.5s Response Time)
> Unlimited PoW @ 0.01 NANO each.

More Info: https://pow.nano.to

![line](https://github.com/fwd/n2/raw/master/.github/line.png)

## Nano.to Support

- Email: support@nano.to
- Twitter: [@nano2dev](https://twitter.com/nano2dev)
- @nano2dev on [Nano's Discord](https://discord.com/invite/RNAE2R9) 

![line](https://github.com/fwd/n2/raw/master/.github/line.png)

## Contributing

Give a ⭐️ if this project helped you!

Contributions, issues and feature requests are welcome at [issues page](https://github.com/fwd/nano-to/issues).

## Nano.to License

**Limited Commercial Use:**

- ✅ Personal & Open Source
- ✅ Commercial use where Nano.to Usernames and/or Checkout is **NOT** the end-product.
- ❌ Commercial use where Nano.to Usernames and/or Checkout **IS** the end-product.

## Stargazers

[![Stargazers over time](https://starchart.cc/fwd/nano-to.svg)](https://github.com/fwd/nano-to)
