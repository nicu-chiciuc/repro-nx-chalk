
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
