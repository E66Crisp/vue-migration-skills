---
name: vue-migration-build
description: Use @vue/compat migration build to upgrade Vue 2 apps to Vue 3 with configurable compat and per-component opt-in.
---

# Migration Build (@vue/compat)

`@vue/compat` is a Vue 3 build that provides Vue 2–compatible behavior by default and emits runtime warnings for deprecated/changed usage. Use it when upgrading a Vue 2 app or library to Vue 3.

## When to Use

- Upgrading a Vue 2 app to Vue 3 (with known limitations)
- Migrating a library to support Vue 3
- Learning Vue 3 differences while still on Vue 2–style APIs

## Setup (Vite)

```js
// vite.config.js
export default {
  resolve: {
    alias: {
      vue: '@vue/compat'
    }
  },
  plugins: [
    vue({
      template: {
        compilerOptions: {
          compatConfig: { MODE: 2 }
        }
      }
    })
  ]
}
```

Dependencies: `vue@^3.1`, `@vue/compat@^3.1`, `@vue/compiler-sfc` (replace `vue-template-compiler`). Alias `vue` to `@vue/compat` and set `compilerOptions.compatConfig.MODE: 2`.

## Compat Configuration

**Global:** use `configureCompat()` from the app entry.

```js
import { configureCompat } from 'vue'

configureCompat({
  FEATURE_ID_A: false,  // disable compat for a feature
  MODE: 3,              // default to Vue 3, enable compat only for listed features
  FEATURE_ID_B: true
})
```

**Per-component:** use `compatConfig` option (same shape as `configureCompat`).

```js
export default {
  compatConfig: { MODE: 3, FEATURE_ID: true },
  // ...
}
```

**Compiler-only:** options starting with `COMPILER_` must be set in build `compilerOptions`, not at runtime (e.g. `COMPILER_V_IF_V_FOR_PRECEDENCE`).

## Upgrade Workflow (Summary)

1. Update deps and alias; enable compat in build.
2. Fix compile-time errors (e.g. filters).
3. Update transition class names (e.g. `.v-enter` → `.v-enter-from`).
4. Switch to `createApp()` and `app.mount()`.
5. Upgrade vuex to v4, vue-router to v4.
6. Fix runtime warnings; use per-component `compatConfig` where needed.
7. When clean, remove `@vue/compat` and use Vue 3 directly.

## Limitations

- Dependencies that rely on Vue 2 internals or private VNode props may not work.
- No IE11 support in Vue 3.
- SSR migration is non-trivial; prefer Vite + `@vue/server-renderer`.

<!--
Source references:
- https://v3-migration.vuejs.org/migration-build.html
- sources/vue-migration/src/migration-build.md
-->
