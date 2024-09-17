> JSBox has ability to handle QRCode

# $qrcode.encode(string)

Encode a string to QRCode image:

```js
const image = $qrcode.encode("https://apple.com");
```

# $qrcode.decode(image)

Decode a string from QRCode image:

```js
const text = $qrcode.decode(image);
```

# $qrcode.scan(function)

Scan QRCode with camera:

```js
$qrcode.scan(text => {
  
})
```

We could provide `cancelled` callback:

```js
$qrcode.scan({
  useFrontCamera: false, // Optional
  turnOnFlash: false, // Optional
  handler(string) {
    $ui.toast(string)
  },
  cancelled() {
    $ui.toast("Cancelled")
  }
})
```