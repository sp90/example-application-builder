# ExampleApplicationBuilder

This is to showcase thew new build system in angular - i would love to take a PR on running the server with one of the following webframeworks

- [uWebSockets.js](https://github.com/uNetworking/uWebSockets)
- [Elysia.js](https://elysiajs.com/)
- [Hono](https://hono.dev/getting-started/bun)

Lets create a folder with alternative server.ts files and make an angular ssr benchmark

## Commands

- Dev SSR: `npm run dev:ssr`
- Build SSR: `npm run build:ssr`
- Serve SSR: `npm run serve:ssr`

## This uses

- `angular@next`
- `angular/ssr@next`
- The CommonEngine from `angular/ssr` 

## Footnotes

This is basically a project generated with 

- `ng new appName --standalone --skip-tests`
- `ng add @angular/ssr`

Then its upgraded to version 17 using

- `ng update @angular/core@next @angular/cli@next` with the force command because angular/ssr is not compatable with v17 of the core
- Patch angular/ssr version in the package-json and `npm i`

Then updating the following files

- `angular.json` - here the config is taken from the angular internal example that was shared as a screenshot
- `server.ts` - same here [example-file](https://github.com/angular/angular-cli/blob/8f9a0d70cdf692b19574410cebb4d029056263fc/packages/angular/ssr/schematics/ng-add/files/server-builder/server.ts.template#L4)
- `tsconfig.app.js` - added main.server.ts to includes (IMPORTANT do not add for files)

## Useful info
- Wanna learn about the [CommonEngine](https://github.com/angular/angular-cli/blob/8f9a0d70cdf692b19574410cebb4d029056263fc/packages/angular/ssr/src/common-engine.ts) here is the source to it
- builds is about **1s** for cold start `ng serve`
- `npm run dev:ssr` **~8-10s**
- Changes are **~200ms** on the initial package
- `npm run build:ssr` **~8-10s**
  
