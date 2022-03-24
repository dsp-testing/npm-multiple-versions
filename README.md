# npm-multiple-versions

Node allows multiple versions of the same dependency.

In this project, package.json contains:

```json
"dependencies": {
    "is-accessor-descriptor": "^1.0.0",
    "kind-of": "^3.2.2"
  }
```

`is-accessor-descriptor` requires `kind-of@6.0.0` which you can see in the `package-lock`:

```json
"node_modules/is-accessor-descriptor": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/is-accessor-descriptor/-/is-accessor-descriptor-1.0.0.tgz",
      "integrity": "sha512-m5hnHTkcVsPfqx3AKlyttIPb7J+XykHvJP2B9bZDjlhLIoEq4XoK64Vg7boZlVWYK6LUY94dYPEE7Lh0ZkZKcQ==",
      "dependencies": {
        "kind-of": "^6.0.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
```

Doing an `npm ci` notice in the filesystem something like:

```
node_modules
  is-accessor-descriptor
    node_modules
      kind-of
  kind-of
```

The outer `kind-of` is version 3.2.2. The one nested under `is-accessor-descriptor` is ^6.0.0. 
