# Vendure Qwik Storefront Starter️

An e-commerce storefront for [Vendure](https://www.vendure.io) built with [Qwik](https://qwik.builder.io/) & [Qwik City](https://qwik.builder.io/qwikcity/overview).

👉 [qwik-storefront.vendure.io](https://qwik-storefront.vendure.io)

## Core Web Vitals

<br/>

![pagespeed.web.dev](docs/metrics.png)

<br/>

## To do

- Cart ✅
- Checkout flow ✅
- Search facet filters ✅
- Login ✅
- Account creation ✅
- Customer account management ✅
- SPA-mode navigation ✅
- Set up GraphQL code generation ✅

**Contributions welcome!**

## Development

Development mode uses [Vite's development server](https://vitejs.dev/). During development, the `dev` command will server-side render (SSR) the output.

```shell
npm start # or `yarn start`
```

> Note: during dev mode, Vite may request a significant number of `.js` files. This does not represent a Qwik production build.

## Preview

The preview command will create a production build of the client modules, a production build of `src/entry.preview.tsx`, and run a local server. The preview server is only for convenience to locally preview a production build, and it should not be used as a production server.

```shell
pnpm preview # or `yarn preview`
```

## Production

The production build will generate client and server modules by running both client and server build commands. Additionally, the build command will use Typescript to run a type check on the source code.

```shell
pnpm build # or `yarn build`
```

## i18n

### Marking string for translation

Any string can be marked for translation by using the `$localize` template function like so:

```typescript
export default component$((props: { name: string }) => {
	return <span>{$localize`Hello ${props.name}!`}</span>;
});
```

### Extracting string for translation

The first step in translation is to build the application. Once the artifacts are build the strings can be extracted for translation.

```bash
pnpm build.client
pnpm i18n-extract
```

The result of the commands is `src/locale/message.en.json`.

### Translating strings

Take the resulting string and send them for translation. Produce a file for each language. For example:

```bash
src/locale/message.en.json    # Original strings
src/locale/message.es.json
```

### Sorting translations

Qwik hashes bundles based on the content of the files. This means that if a file changes, the order of i18n translations will be lost and can be difficult to manage manually.

```bash
pnpm i18n-sort
```

The `i18n-sort` script will sort by first appearance in the src folder to keep a consistent order.

### Testing translations

The resulting language should match your browser language. You can also override the language by adding ?lang=es to the URL.

---

## Related

- [Vendure Docs](https://vendure.io/docs)
- [Vendure Github](https://github.com/vendure-ecommerce/vendure)
- [Vendure Discord](https://vendure.io/community)
- [Qwik Docs](https://qwik.builder.io/)
- [Qwik Github](https://github.com/BuilderIO/qwik)
- [@QwikDev](https://twitter.com/QwikDev)
- [Qwik Discord](https://qwik.builder.io/chat)

## Deno Server

This app has a minimal [Deno server](https://deno.com/manual/examples/http_server) implementation. After running a full build, you can preview the build using the command:

```
pnpm serve
```

Then visit [http://localhost:8080/](http://localhost:8080/)

## Vercel Edge

This starter site is configured to deploy to [Vercel Edge Functions](https://vercel.com/docs/concepts/functions/edge-functions), which means it will be rendered at an edge location near to your users.

## Installation

The adaptor will add a new `vite.config.ts` within the `adapters/` directory, and a new entry file will be created, such as:

```
└── adapters/
    └── vercel-edge/
        └── vite.config.ts
└── src/
    └── entry.vercel-edge.tsx
```

Additionally, within the `package.json`, the `build.server` script will be updated with the Vercel Edge build.

## Production build

To build the application for production, use the `build` command, this command will automatically run `pnpm build.server` and `pnpm build.client`:

```shell
pnpm build
```

[Read the full guide here](https://github.com/BuilderIO/qwik/blob/main/starters/adapters/vercel-edge/README.md)

## Dev deploy

To deploy the application for development:

```shell
pnpm deploy
```

Notice that you might need a [Vercel account](https://docs.Vercel.com/get-started/) in order to complete this step!

## Production deploy

The project is ready to be deployed to Vercel. However, you will need to create a git repository and push the code to it.

You can [deploy your site to Vercel](https://vercel.com/docs/concepts/deployments/overview) either via a Git provider integration or through the Vercel CLI.
