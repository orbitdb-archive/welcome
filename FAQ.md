# Frequently Asked Questions

This document should be a living file, outlining questions and good answers for how OrbitDB works. If a question is no longer relevant, or could be written better, or hasn't been asked or answered, please open a Pull Request or an Issue, and let's fix that!

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [How is a node address sufficient for communicating with a remote database?](#how-is-a-node-address-sufficient-for-communicating-with-a-remote-database)
- [Contribute](#contribute)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### How is a node address sufficient for communicating with a remote database?

It depends on your IPFS setup — The IPFS network is used to store the data and thus content-routing and communication relies on how you setup and use IPFS. For instance, DHT content-routing, a big part of connectivity magic, is not fully operational in the JS implementation but working in the Go implementation. Thus, in the JS implementation its helpful to [configure a shared signalling server](https://ipfs.io/ipfs/QmY2LufsW3v6AfxTTkp6SGqDGa5AeJhSZXH8RSsdiao4Ds/) so that your nodes can find each other.

**Brief overview of OrbitDBAddress as it relates to IPFS:**
The *magic* and crux of an OrbitDBAddress is the hash part, which is an IPFS [Multihash](https://github.com/multiformats/multihash). The hash is used to retrieve a [database manifest](https://github.com/orbitdb/orbit-db/blob/master/GUIDE.md#manifest), and subsequently an access controller. Both of which are objects stored on IPFS which is a content-addressable storage system. The hash in the OrbitDBAddress points to the database manifest and inside the database manifest is another hash that points to the Access Controller.

To replicate the entries in the database, the OrbitDBAddress is used as a topic on IPFS PubSub to exchange [heads](https://github.com/orbitdb/ipfs-log/blob/master/API.md#heads) which can be used to retrieve the rest of the entries as each entry links to the previous one, see [IPFS-Log](https://github.com/orbitdb/ipfs-log). 

Hope I understood your question correctly and provided a helpful answer 🥂 

_Originally asked by @CaptainQuark in [orbit-db#440](https://github.com/orbitdb/orbit-db/issues/440). Answer from @mistakia._

### Contribute

Please do! If you think this could be improved in any way, add an answer or a question here.

Do you think that we should use a different FAQ system? Awesome. Open an issue suggesting what you think would work better.

