# rn-electrum-client

Electrum Protocol Client for React Native

# based on

* https://github.com/you21979/node-electrum-client
* https://github.com/7kharov/node-electrum-client

# features

* persistence (ping strategy and reconnection)
* batch requests
* works in RN and nodejs

## protocol spec

* https://electrumx-spesmilo.readthedocs.io/en/latest/protocol.html

## usage

Relies on `react-native-tcp` so it should be already installed and linked in RN project. `net` & `tls` dependencies should be
injected via constructor, this library won't do `require('net')`.
For RN you can place it in `shim.js`:

```javascript
  global.net = require('react-native-tcp');
```

For nodejs simply

```javascript
  const net = require('net');
```

and then

```javascript
  const client = new ElectrumClient(net, false, 50001, 'electrum1.bluewallet.io', 'tcp');
  const ver = await client.initElectrum({ client: 'bluewallet', version: '1.4' });
  const balance = await client.blockchainScripthash_getBalance('716decbe1660861c3d93906cb1d98ee68b154fd4d23aed9783859c1271b52a9c');
```
