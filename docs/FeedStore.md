# orbit-db-feedstore

[![npm version](https://badge.fury.io/js/orbit-db-feedstore.svg)](https://badge.fury.io/js/orbit-db-feedstore)
[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/orbitdb/Lobby) [![Matrix](https://img.shields.io/badge/matrix-%23orbitdb%3Apermaweb.io-blue.svg)](https://riot.permaweb.io/#/room/#orbitdb:permaweb.io) [![Discord](https://img.shields.io/discord/475789330380488707?color=blueviolet&label=discord)](https://discord.gg/cscuf5T)

> Log database for orbit-db

A log database with traversable history. Entries can be added and removed. Useful for *"shopping cart"* type of use cases, or for example as a feed of blog posts or *"tweets"*.

Used in [orbit-db](https://github.com/haadcode/orbit-db).

## Table of Contents

- [Install](#install)
- [Usage](#usage)
- [API](#api)
- [Contributing](#contributing)
- [License](#license)

## Install

This project uses [npm](https://npmjs.com) and [node](https://nodejs.org)

```sh
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

Get a feed database and add an entry to it:

```javascript
const feed = await orbitdb.feed('haad.posts')
feed.add({ title: 'Hello', content: 'World' })
  .then(() => {
    const posts = feed.iterator().collect()
    posts.forEach((post) => {
      let data = post.payload.value
      console.log(data.title + '\n', data.content)
      // Hello
      //  World   
    })
  })
```

Later, when the database contains data, load the history and query when ready:

```javascript
const feed = await orbitdb.feed('haad.posts')
feed.events.on('ready', () => {
  const posts = feed.iterator().collect()
  posts.forEach((post) => console.log(post.title + '\n', post.content))
  // Hello
  // World  
})
```

## API

See [orbit-db's API Documenations](https://github.com/orbitdb/orbit-db/blob/master/API.md#feedname) for full details.

## Contributing

If you think this could be better, please [open an issue](https://github.com/orbitdb/orbit-db-feedstore/issues/new)!

Please note that all interactions in [@orbitdb](https://github.com/orbitdb) fall under our [Code of Conduct](CODE_OF_CONDUCT.md).

Note: Tests for this repo are in the [`orbit-db`](https://github.com/orbitdb/orbit-db) repository.

## License

[MIT](LICENSE) © 2016-2020 Protocol Labs Inc., Haja Networks Oy
