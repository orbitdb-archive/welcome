# orbit-db-counterstore

[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/orbitdb/Lobby) [![Matrix](https://img.shields.io/badge/matrix-%23orbitdb%3Apermaweb.io-blue.svg)](https://riot.permaweb.io/#/room/#orbitdb:permaweb.io) [![Discord](https://img.shields.io/discord/475789330380488707?color=blueviolet&label=discord)](https://discord.gg/cscuf5T)
[![npm version](https://badge.fury.io/js/orbit-db-counterstore.svg)](https://badge.fury.io/js/orbit-db-counterstore)

> Counters database for OrbitDB

A simple counters database. Useful for example counting events separate from data.

Used in [orbit-db](https://github.com/orbitdb/orbit-db).

## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [API](#api)
- [Contribute](#contribute)
  - [Linting](#linting)
- [License](#license)

## Install

This project uses [npm](https://npmjs.com) and [nodejs](https://nodejs.org)

```
npm install orbit-db ipfs
```

## Usage

First, create an instance of OrbitDB:

```javascript
const IPFS = require('ipfs')
const OrbitDB = require('orbit-db')

const ipfs = new IPFS()
const orbitdb = OrbitDB.createInstance(ipfs)
```

Get a log database and add an entry to it:

```javascript
const counter = await orbitdb.counter('visitors')
await counter.inc()
console.log(counter.value)
// 1
await counter.inc(4)
console.log(counter.value)
// 5
```

Later, when the database contains data, load the history and query when ready:

```javascript
const counter = await orbitdb.counter('visitors')
counter.events.on('ready', () => {
  await counter.inc()
  console.log(counter.value)
  // 6
})
```

See [example/index.html](https://github.com/orbitdb/orbit-db-counterstore/blob/master/example/index.html) for a detailed example. Note that to run this example, you need to have a local [IPFS daemon](https://dist.ipfs.io/go-ipfs/floodsub-2) [running](https://ipfs.io/docs/getting-started/) at port 5001.

## API

See [OrbitDB's API Documentation](https://github.com/orbitdb/orbit-db/blob/master/API.md#countername) for full details.

## Contribute

Please, feel free to contribute! Take a look at [the issues](https://github.com/orbitdb/orbit-db-counterstore/issues), and comment on an existing issue or create a new one if you have questions, bugs, or suggestions. For larger PRs, open an issue first if you could - drive-by PRs are also welcomed.

Please abide by the [Code of Conduct](CODE_OF_CONDUCT.md). For more on contributing to OrbitDB, check out the docs in [orbitdb/welcome](https://github.com/orbitdb/welcome).

## License

[MIT](LICENSE) © 2016-2018 Protocol Labs Inc., Haja Networks Oy
