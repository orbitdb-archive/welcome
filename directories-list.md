# Directories List

## @OrbitDB

- [awesome-orbitdb](https://github.com/orbitdb/awesome-orbitdb)

This was an attempt to list everything that is using orbitdb, or could help people. Basically, what has been built?

- [crdts](https://github.com/orbitdb/crdts)

Library for CRDTS. JavaScript. Npm module. Used in orbit-db-counterstore. Mostly just one function is used.

- [example-orbitdb-todomvc](https://github.com/orbitdb/example-orbitdb-todomvc)

Someone is working on this. We should support that!

- [ipfs-log](https://github.com/orbitdb/ipfs-log)

Bread and butter. The most important module used by OrbitDB. JS npm.

- [orbit](https://github.com/orbitdb/orbit)

Orbit Chat. Needs to be revamped, should probably be renamed. Might be worth separating into a different org. Not an npm module. This is a landing page repo.

- [orbit-bot](https://github.com/orbitdb/orbit-bot)

A bot for orbit chat

- [orbit-core](https://github.com/orbitdb/orbit-core)

The core of orbit chat. Orbit/orbit is the main repo for orbit chat. Orbit core is the JavaScript npm module that implements the orbit-chat protocol.

- [orbit-db](https://github.com/orbitdb/orbit-db)

The main repo for orbit db. The other bread and butter.

- [orbit-db-cache](https://github.com/orbitdb/orbit-db-cache)

Module that orbitdb uses. JS, npm. Actually a persistency layer, not a cache. Saves the latest HEAD of each db locally into levelDB. Doesn't store a huge amount of data, just the amount of DBs you have. For all of the dbs you have locally, you have a hash for each.

- [orbit-db-cli](https://github.com/orbitdb/orbit-db-cli)

CLI for orbit-db.

- [orbit-db-counterstore](https://github.com/orbitdb/orbit-db-counterstore)

Datastore in orbitdb. Uses CRDTs, inherits from orbit-db-store. Why is it called counterstore and not CRDTstore? Because it is only a counter - it uses CRDTs for that. Only for gcounter, more specifically.

- [orbit-db-docstore](https://github.com/orbitdb/orbit-db-docstore)

Another orbit-db store which allows you to index a blob. npm js.

- [orbit-db-eventstore](https://github.com/orbitdb/orbit-db-eventstore)

Another data model type. Like IPFS log. Wraps into a store interface.

- [orbit-db-feedstore](https://github.com/orbitdb/orbit-db-feedstore)

Database type in orbitdb, exactly like eventlog, but you can delete events from the log. Twitter feed you can delete your entries - this is the same.

- [orbit-db-keystore](https://github.com/orbitdb/orbit-db-keystore)

Keystore is actually a module that stores the keys locally. You can generate keys, it persists them in the data folder, you can import and export keys - it is basically a key manager.

- [orbit-db-kvstore](https://github.com/orbitdb/orbit-db-kvstore)

KeyValue store. Another DB type in OrbitDB. May be unclear in the code, where `kvstore` is called `keyvalue` store.

- [orbit-db-pubsub](https://github.com/orbitdb/orbit-db-pubsub)

A layer between orbitdb and IPFS Pubsub. Basically is the message broker of Orbitdb that handles all fo the communication. Distributed pubsub. Every update goes through this. Every orbitdb address is a channel in pubsub, and when you open the database you join that pubsub channel.

- [orbit-db-store](https://github.com/orbitdb/orbit-db-store)

This is a base calls for all datastores in orbitdb. A Base Class defines the common interface for all databases. We should refactor this - it should not be a base class, but a composting (?). We'll figure this out. The Stores are the API of that database; they also contian the index so that if you cac he anything in the memory, the user never actually directly asks the index, but the API of the store. All of these stores use -- they're very simple, there's no io or so on. The store is where that happens. Every store calls this operation which calls the log, and so on, and eventually sends a cb somewhere saying that it is persisted. It has a load method that checks the cache, then ... I lost it. The base class hooks the orbitdb main thing, that contains the messaging and the keystore and the access-controller with the log and the form and so on with the indices.

- [orbit-electron](https://github.com/orbitdb/orbit-electron)

Desktop application for OrbitChat. Uses Orbit Core and IPFS. Hasn't been updated in over a year. Run `npm audit`.

- [orbit-textui](https://github.com/orbitdb/orbit-textui)

A terminal client for orbit chat. (As opposed to orbitdb-cli, which is for orbitdb.)

- [orbit-web](https://github.com/orbitdb/orbit-web)

Browser client of orbit chat. This is the most important client one for marketing and community purposes.

- [orbitdb-orbit-crypto](https://github.com/orbitdb/orbitdb-orbit-crypto)

May not be used by anything. Needs to be checked by @haadcode.

- [research](https://github.com/orbitdb/research)

Research on decentralized databases. Papers, etc. Doc.

- [welcome](https://github.com/orbitdb/welcome)

Community repo.

## @haadcode

- [example-orbitdb-webpack](https://github.com/haadcode/example-orbitdb-webpack)

Move to OrbitDB. An example how to use orbitdb through webpack.

- [go-ipfs-log](https://github.com/haadcode/go-ipfs-log)

Prototype, long time ago, not finished. @kex has some go-ipfs stuff, too. Keep. Contact Kex.

- [immutabledb](https://github.com/haadcode/immutabledb)

A way of doing a datastore, to use everything. Can store quite a bit of things. Instead of using IPFS, use anything else.

- [ipfs-daemon](https://github.com/haadcode/ipfs-daemon)

Delete.

- [ipfs-post](https://github.com/haadcode/ipfs-post)

Datastructure for orbit-chat post. Move and rename.

- [logplease](https://github.com/haadcode/logplease)
- [orbit-db-channelstore](https://github.com/haadcode/orbit-db-channelstore)

Prototype of channelstore. Move.

- [orbit-db-http-server](https://github.com/haadcode/orbit-db-http-server)

Move.

- [orbit-server](https://github.com/haadcode/orbit-server)

Delete.

- [planet-express](https://github.com/haadcode/planet-express)

Twitter prototype. May have some screenshots. Kind of cool.

- [pouchdb-adapter-orbitdb](https://github.com/haadcode/pouchdb-adapter-orbitdb)

Haad will look into it.

- [proto2](https://github.com/haadcode/proto2)

Visualization of orbitdb's dataflow and functions that may not work. Out of date.

## Shipyard has some modules

Pubsub-peer-monitor

## TODO

- Add note to Global contribute about asking to work on PRs and how long you have before we follow up.
- Set up an npm org.
- Open an issue about github.com/orbit being renamed to orbitchat.
- Fix [orbit](). Ask Klaus? Someone needs to fix this.