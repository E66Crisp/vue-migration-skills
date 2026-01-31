---
name: vue-migration-global-api
description: Migrate Vue 2 global API to Vue 3 app instance (createApp, config, prototype, extend).
---

# Global API → App Instance

Vue 3 replaces global APIs with an **app instance** from `createApp()`. Any API that globally mutated Vue is now on the app instance.

## Entry and mount

```js
// Vue 2
new Vue({ el: '#app', ... })
// or
const app = new Vue({ ... })
app.$mount('#app')

// Vue 3
import { createApp } from 'vue'
const app = createApp(RootComponent)
app.mount('#app')
```

## API mapping

| Vue 2 global | Vue 3 (app instance) |
|--------------|----------------------|
| `Vue.config` | `app.config` |
| `Vue.config.ignoredElements` | `app.config.compilerOptions.isCustomElement` (function) |
| `Vue.component` | `app.component` |
| `Vue.directive` | `app.directive` |
| `Vue.mixin` | `app.mixin` |
| `Vue.use` | `app.use` |
| `Vue.prototype` | `app.config.globalProperties` |
| `Vue.extend` | Removed; use options object + `createApp` or `defineComponent` for types |

## Important changes

- **`Vue.prototype` → `app.config.globalProperties`**  
  Prefer `provide`/`inject` for app-wide values when possible.

- **`Vue.extend` removed**  
  Use a plain options object with `createApp(Options).mount(...)`. For TypeScript, use `defineComponent(Options)`. For inheritance, use the `extends` option or Composition API.

- **`config.ignoredElements` → `config.compilerOptions.isCustomElement`**  
  Must be a function: `(tag) => tag.startsWith('ion-')`. With runtime-only build, set this in the build config (e.g. vue-loader / Vite), not at runtime.

- **Plugins**  
  No more auto-install via `Vue.use` in UMD. Users must call `app.use(Plugin)`.

## Sharing config across apps

Use a factory that creates an app and applies the same components/directives/provides:

```js
const createMyApp = (root) => {
  const app = createApp(root)
  app.directive('focus', { mounted: (el) => el.focus() })
  return app
}
createMyApp(Foo).mount('#foo')
createMyApp(Bar).mount('#bar')
```

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/global-api.html
- sources/vue-migration/src/breaking-changes/global-api.md
-->
