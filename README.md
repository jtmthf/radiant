# Radiant

If [After.js](https://github.com/jaredpalmer/after.js/), [Sapper](https://github.com/sveltejs/sapper) and [React Apollo](https://github.com/apollographql/react-apollo) had a baby...

## Project Goals / Philosophy / Requirements

After.js is awesome. However I believe fully dynamic route configs are a better approach. If you prefer static route configs, I highly recommend you check out After.js over Radiant.

* Routes are just components, but can optionally be defined by folder structure for
  zero-boilerplate routing and code-splitting.
* Next.js's `getInitialProps` was/is a brilliant idea. Radiant expands on this
  concept by adding the ability to simultaneously fetch components and run `getInitialProps` for faster page loads that haven't been prefetched. Furthermore
  Radiant's first class integration with Apollo allows for seamless prefetching of GraphQL data.
* Route-based code-splitting should come for free or be easy to opt into.
* Route-based transitions / analytics / data loading / preloading etc. , should either come for free or be trivial to implement on your own.
* Must be TypeScript first, but must be easy to add Babel optionally. IMHO TypeScript is underrated as a JavaScript compiler and can fully replace Babel except in cases of needing custom Babel plugins. Furthermore it's about time there was a solid TypeScript first React framework.
* Generally, everything should come with the battery pack included, but be overridable.

## Getting Started

Yarn users

```bash
yarn add -D @radiant/scripts
yarn add @radiant/core @radiant/router @radiant/head
```

NPM users

```bash
npm i -D @radiant/scripts
npm i @radiant/core @radiant/router @radiant/head
```

In your `package.json`, add the following:

```json
{
  "scripts": {
    "start": "radiant-scripts start",
    "test": "radiant-scripts test --env=jsdom",
    "build": "radiant-scripts build",
    "start:prod": "NODE_ENV=production node build/server.js"
  }
}
```

Create a file called `tsconfig.json` in your project's root.

```json
// ./tsconfig.json
{
  "extends": "./node_modules/@radiant/scripts/dist/tsconfig.json"
}
```

Create a folder called `src` in your project's root. Inside of `src` create a new folder called `routes`. For demo purposes, create two React components in `./src/routes/index.tsx` and `./src/routes/about.tsx`.

```tsx
// ./src/routes/index.tsx
import React from "react";
import { NavLink } from "@radiant/router";

class Home extends React.Component {
  render() {
    return (
      <div>
        <NavLink to="/">Home</NavLink>
        <NavLink to="/about">About</NavLink>
        <h1>Home</h1>
      </div>
    );
  }
}

export default Home;
```

```tsx
// ./src/routes/about.tsx
import * as React from "react";
import { NavLink } from "@radiant/router";

class About extends React.Component {
  render() {
    return (
      <div>
        <NavLink to="/">Home</NavLink>
        <NavLink to="/about">About</NavLink>
        <h1>About</h1>
      </div>
    );
  }
}

export default About;
```

Now run `yarn start` or `npm start` and open `localhost:3000`. You'll have an SSR React / React
Router 4 application.

Below is a list of commands you will probably find useful.

* `yarn start` or `npm start`: Runs the project in development mode. You can view your application at `http://localhost:3000`. The page will reload if you make edits.
* `yarn build` or `npm run build`: Builds the app for production to the build folder.
* `yarn start:prod` or `npm run start:prod`: Runs the compiled app in production. You can again view your application at `http://localhost:3000`
* `yarn test` or `npm test`: Runs the test watcher (Jest) in an interactive mode. By default, runs tests related to files changed since the last commit.
* `yarn start -- --inspect` or `npm start -- --inspect`: To debug the node server, you can use `radiant start --inspect`. This will start the node server and enable the inspector agent. For more information, see [this](https://nodejs.org/en/docs/inspector/).
* `yarn start -- --inspect-brk` or `npm start -- --inspect-brk`: To debug the node server, you can use `radiant start --inspect-brk`. This will start the node server, enable the inspector agent and Break before user code starts. For more information, see [this](https://nodejs.org/en/docs/inspector/).

## Comparisons

Radiant is designed after many popular JavaScript frameworks, and as such I am forever thankful for their inspiration. Here are a few comparisons to other popular frameworks.

### Comparison with Next.js

### Comparison with After.js

### Comparison with Sapper

### Comparison with Gatsby

### Comparison with Create React App

### Comparison with Razzle

### Comparison with Preact-CLI
