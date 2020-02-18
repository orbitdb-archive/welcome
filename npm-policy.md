# The npm policy

We use [npmjs](https://www.npmjs.com/) to publish our JavaScript packages. This document outlines how we use it.

- [Team permissions](#team-permissions)
- [Minimal viable `package.json`](#minimal-viable-packagejson)
- [Naming conventions](#naming-conventions)
- [2FA](#2fa)

### Team permissions

We do not use an @OrbitDB team for scoping packages, due to issues with republishing scoped packages and the long nature of `@orbitdb/orbit-db` as an annoying name to type. Instead, publish under your own name.

However; ensure that you grant publishing rights to another core contributor. The way to do this is to use [`npm owner add @user`](https://docs.npmjs.com/cli/owner). They must already have push access to the repository on GitHub.

When you do this, add this user as a `maintainer` in the `localMaintainers` field. This ensures that everyone knows who is able to publish the package. The `localMaintainers` field is an Array and can take multiple users. Minimally add their NPM name.

```json
{
  "localMaintainers": [
    "richlitt"
  ]
}
```

Npm automatically creates a `maintainer` field, which isn't shown publicly in the [`package.json`](https://docs.npmjs.com/files/package.json), and which matches the output of `$ npm info`. In order to avoid name collisions and possible issues down the road, we use a custom field to hold this data. The `localMaintainers` field should always match the output of `$ npm info`. The printout looks like this:

```sh
@orbitdb/example-orbitdb-webpack@0.0.2 | MIT | deps: 1 | versions: 2

...

maintainers:
- richardlitt <richard.littauer@gmail.com>
```

If you do not add an `localMaintainers` field to the `package.json`, we will assume that there is no other maintainer, and you will be bugged by the community administrator and other developers (please) to add one. :) This is important, for a variety of reasons: [bus factor](https://en.wikipedia.org/wiki/Bus_factor), ease of publishing, ease of access, and working in the public as a maintainer.

When adding a new user as a maintainer, open a pull request with this change. This publicly states that that person will now be a maintainer for the repository, telling all watchers that another user has been trusted. Add them as maintainers to the package only _after_ the PR has been merged.

Likewise, when removing access from a maintainer, do so with a PR, removing them, and then remove their access using the npm cli.

### Minimal viable `package.json`

* `engines`, `scripts`, `dependencies`, `devDependencies`, and other computational fields are as needed. The rest, however, illustrates the metadata we should have:
* The `description` should match the GitHub description.
* The name should match the repository name.
* `contributors` can be excluded if there is a separate `CONTRIBUTORS.md`, or if there is an `AUTHORS` file.
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

This is required if you have publishing rights to any package. You can learn more about how it works on npm [here](https://docs.npmjs.com/about-two-factor-authentication).
