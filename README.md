This repo describes a build issue in the the 5.2.4-beta.2 release of algoliasearch

Steps to reproduce issue run the following

| Note: you will need pnpm installed

```
pnpm install
pnpm build
```

The following is the output when building

```bash
vite v5.4.2 building for production...
✓ 38 modules transformed.
x Build failed in 230ms
error during build:
node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js (208:9): "Region" is not exported by "node_modules/.pnpm/@algolia+client-abtesting@5.2.4-beta.2/node_modules/@algolia/client-abtesting/dist/builds/browser.js", imported by "node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js".
file: /path/to/repo/algoliasearch-issue/node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js:208:9

206: __reExport(models_exports, client_analytics_star);
207: __reExport(models_exports, client_abtesting_star);
208: import { Region as ABTestingRegion } from "@algolia/client-abtesting";
              ^
209: import { Region as AnalyticsRegion } from "@algolia/client-analytics";
210: import {

    at getRollupError (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/parseAst.js:392:41)
    at error (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/parseAst.js:388:42)
    at Module.error (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:13967:16)
    at Module.traceVariable (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:14414:29)
    at ModuleScope.findVariable (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:12121:39)
    at ReturnValueScope.findVariable (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:7467:38)
    at FunctionBodyScope.findVariable (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:7467:38)
    at Identifier.bind (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:6941:40)
    at ArrowFunctionExpression.bind (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:4808:23)
    at Property.bind (file:///path/to/repo/algoliasearch-issue/node_modules/.pnpm/rollup@4.21.2/node_modules/rollup/dist/es/shared/node-entry.js:4808:23)
 ELIFECYCLE  Command failed with exit code 1.

```

The following is the output from another (nextjs) project

```bash
Failed to compile.

../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
Attempted import error: 'Region' is not exported from '@algolia/client-abtesting' (imported as 'ABTestingRegion').

Import trace for requested module:
../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
./src/utils/algolia/client.ts
./src/utils/algolia/search.ts

../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
Attempted import error: 'AbtestingClient' is not exported from '@algolia/client-abtesting' (imported as 'AbtestingClient').

Import trace for requested module:
../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
./src/utils/algolia/client.ts
./src/utils/algolia/search.ts

../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
Attempted import error: 'AdvancedSyntaxFeatures' is not exported from '@algolia/client-search' (imported as 'AdvancedSyntaxFeatures').

Import trace for requested module:
../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
./src/utils/algolia/client.ts
./src/utils/algolia/search.ts

../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
Attempted import error: 'AlternativesAsExact' is not exported from '@algolia/client-search' (imported as 'AlternativesAsExact').

Import trace for requested module:
../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
./src/utils/algolia/client.ts
./src/utils/algolia/search.ts

../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
Attempted import error: 'AnalyticsClient' is not exported from '@algolia/client-analytics' (imported as 'AnalyticsClient').

Import trace for requested module:
../../node_modules/.pnpm/algoliasearch@5.2.4-beta.2/node_modules/algoliasearch/dist/browser.js
./src/utils/algolia/client.ts
./src/utils/algolia/search.ts


> Build failed because of webpack errors
```
