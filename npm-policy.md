# The npm policy

We use [npmjs](https://www.npmjs.com/) to publish our JavaScript packages. This document outlines how we use it.

- [Team permissions](#team-permissions)
- [Minimal viable `package.json`](#minimal-viable-packagejson)
- [Naming conventions](#naming-conventions)
- [2FA](#2fa)

### Team permissions

We do not use an @OrbitDB team for scoping packages, due to issues with republishing scoped packages and the long nature of `@orbitdb/orbit-db` as an annoying name to type. Instead, publish under your own name.

However; ensure that you grant publishing rights to another core contributor. The way to do this is to use [`npm owner add @user`](https://docs.npmjs.com/cli/owner).

When you do this, add this user as `maintainer` in the `maintainer` field. This ensures that everyone knows who is able to publish the package. The `maintainer` field is an Array and can take multiple users. Minimally add their NPM name.

If you do not add a `maintainer` field to the `package.json`, we will assume that there is no other maintainer, and you will be bugged by the community administrator and other developers (please) to add one. :) This is important, for a variety of reasons: bus factor, ease of publishing, ease of access, and working in the public as a maintainer.

When adding a new user as a maintainer, do so in a PR. This publicly states that that person will now be a maintainer for the repository, telling all watchers that another user has been trusted.

### Minimal viable `package.json`

* `engines`, `scripts`, `dependencies`, `devDependencies`, and other computational fields are as needed. The rest, however, illustrates the metadata we should have:
* The `description` should match the GitHub description.
* The name should match the repository name.
* `contributors` can be excluded if there is a separate `CONTRIBUTORS.md`.
* The `keywords` should generally match the Github topics.

```json
{
  "name": "orbit-db",
  "version": "0.19.9",
  "description": "Distributed p2p database on IPFS",
  "author": "Haad",
  "license": "MIT",
  "repository": {
    "type": "git",
    "url": "https://github.com/orbitdb/orbit-db"
  },
  "main": "src/OrbitDB.js",
  "dependencies": {},
  "devDependencies": {},
  "scripts": {},
  "bugs": "https://github.com/orbitdb/orbit-db/issues",
  "homepage": "https://github.com/orbitdb/orbit-db",
  "keywords": [
    "p2p",
    "distributed",
    "decentralized",
    "database",
    "ipfs",
    "crdt",
    "peer-to-peer",
  ],
  "contributors": [
    "Haadcode",
    "RichardLitt"
  ],
  "maintainers": [
    "richlitt",
    "haadcode"
  ]
}
```

### Naming conventions

We preface all of our packages with `orbit-`, `orbit-db` or `orbit-web-`, depending on the use case. For packages which will not be required in the ecosystem, or which are not solely orbit related, these prefixes can be dropped.

### 2FA

Enable it.
