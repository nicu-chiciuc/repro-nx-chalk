
## Generated using

### Create nx workspace

https://nx.dev/tutorials/integrated-repo-tutorial

```
npx create-nx-workspace@latest repro-nx-chalk --preset=ts
```

Select `no` for cache config.

### Add @nx/node plugin

https://nx.dev/packages/node

```
npm install -D @nx/node

nx g @nx/node:application my-new-app

```

select `none` for framework

`nx serve my-new-app` works now.


### Install ESM-only package

```
npm install chalk
```

and import it in `src/main.ts`


```ts
import Chalk from 'chalk';

console.log(Chalk.red('Hello World!'));
```

`nx serve my-new-app` fails with

```
❯ nx serve my-new-app

> nx run my-new-app:serve:development

Debugger listening on ws://localhost:9229/43c0228f-4cbf-4c00-b598-48810f8403b2
Debugger listening on ws://localhost:9229/43c0228f-4cbf-4c00-b598-48810f8403b2
For help, see: https://nodejs.org/en/docs/inspector



/path/repro-nx-chalk/node_modules/@nx/js/src/executors/node/node-with-require-overrides.js:18
        return originalLoader.apply(this, arguments);
                              ^
Error [ERR_REQUIRE_ESM]: require() of ES Module /path/repro-nx-chalk/node_modules/chalk/source/index.js from /path/repro-nx-chalk/dist/packages/my-new-app/packages/my-new-app/src/main.js not supported.
Instead change the require of index.js in /path/repro-nx-chalk/dist/packages/my-new-app/packages/my-new-app/src/main.js to a dynamic import() which is available in all CommonJS modules.
    at Module._load (/path/repro-nx-chalk/node_modules/@nx/js/src/executors/node/node-with-require-overrides.js:18:31)
    at Object.<anonymous> (/path/repro-nx-chalk/dist/packages/my-new-app/packages/my-new-app/src/main.js:23:28)
    at Module._load (/path/repro-nx-chalk/node_modules/@nx/js/src/executors/node/node-with-require-overrides.js:18:31)
    at Object.<anonymous> (/path/repro-nx-chalk/dist/packages/my-new-app/main.js:42:1)
    at Module._load (/path/repro-nx-chalk/node_modules/@nx/js/src/executors/node/node-with-require-overrides.js:10:31)
```
