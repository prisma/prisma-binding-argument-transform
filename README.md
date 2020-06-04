# Prisma binding argument transform

![Build status](https://github.com/prisma/prisma-binding-argument-transform/workflows/CI/badge.svg)

## Installation and Usage

### Installation

Run `yarn add git+https://git@github.com:prisma/prisma-binding-argument-transform.git` or `npm install git+https://git@github.com:prisma/prisma-binding-argument-transform.git` to install it in your project.

### Usage

```ts
// import { makeWherePrisma2Compatible, makeOrderByPrisma2Compatible } from 'prisma-binding-argument-transformer'
const { makeWherePrisma2Compatible, makeOrderByPrisma2Compatible } = require('prisma-binding-argument-transformer')

const resolvers = {
  Query: {
    users: (_, { where, orderBy }) {
      const prisma2Where = makeWherePrisma2Compatible(where)
      const prisma2OrderBy = makeOrderByPrisma2Compatible(orderBy)
      return prisma.user.findMany({
        where: prisma2Where,
        orderBy: prisma2OrderBy,
      })
    }
  }
}
```

## Local Development

### `npm start` or `yarn start`

Runs the project in development/watch mode. Your project will be rebuilt upon changes.

Your library will be rebuilt if you make edits.

### `npm run build` or `yarn build`

Bundles the package to the `dist` folder.
The package is optimized and bundled with Rollup into multiple formats (CommonJS, UMD, and ESM).

### `npm test` or `yarn test`

Runs the test watcher (Jest) in an interactive mode.
By default, runs tests related to files changed since the last commit.
