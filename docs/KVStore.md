# orbit-db-kvstore

[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/orbitdb/Lobby) [![Matrix](https://img.shields.io/badge/matrix-%23orbitdb%3Apermaweb.io-blue.svg)](https://riot.permaweb.io/#/room/#orbitdb:permaweb.io) [![Discord](https://img.shields.io/discord/475789330380488707?color=blueviolet&label=discord)](https://discord.gg/cscuf5T)
[![npm version](https://badge.fury.io/js/orbit-db-kvstore.svg)](https://badge.fury.io/js/orbit-db-kvstore)

> Key-Value database for orbit-db

A key-value database just like your favourite key-value database.

Used in [orbit-db](https://github.com/haadcode/orbit-db).

## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [API](#api)
- [Contributing](#contributing)
- [License](#license)

## Install
```
npm install orbit-db ipfs
```

## Usage

First, create an instance of OrbitDB:

```javascript
const IPFS = require('ipfs')
const OrbitDB = require('orbit-db')

const ipfs = new IPFS()
const orbitdb = await OrbitDB.createInstance(ipfs)
```

Get a key-value database and add an entry to it:

```javascript
const kv = await orbitdb.kvstore('settings')
kv.put('volume', '100')
  .then(() => {
    console.log(kv.get('volume'))
    // 100
  })
```

Later, when the database contains data, load the history and query when ready:

```javascript
const kv = await orbitdb.kvstore('settings')
kv.events.on('ready', () => {
  console.log(kv.get('volume'))
  // 100
})
```

## API

See [orbit-db's API Documenations](https://github.com/haadcode/orbit-db/blob/master/API.md#kvstorename) for full details.

## Contributing

If you think this could be better, please [open an issue](https://github.com/orbitdb/orbit-db-kvstore/issues/new)!

Please note that all interactions in [@orbitdb](https://github.com/orbitdb) fall under our [Code of Conduct](CODE_OF_CONDUCT.md).

## License

[MIT](LICENSE) ©️ 2016-2018 Protocol Labs Inc., 2018 Haja Networks Oy
