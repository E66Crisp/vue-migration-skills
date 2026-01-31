---
name: vue-migration-global-api-treeshaking
description: Use Vue 3 named exports for global APIs (nextTick, reactive, etc.) for tree-shaking.
---

# Global API Treeshaking

Vue 3 exposes former global APIs as **named exports** from `'vue'`. Use them instead of `Vue.*` so unused code can be tree-shaken.

## Usage

```js
// Vue 2
import Vue from 'vue'
Vue.nextTick(() => {})
const state = Vue.observable({})

// Vue 3
import { nextTick, reactive } from 'vue'
nextTick(() => {})
const state = reactive({})
```

## Affected APIs

- `Vue.nextTick` → `import { nextTick } from 'vue'`
- `Vue.observable` → `import { reactive } from 'vue'`
- `Vue.version` → `import { version } from 'vue'`
- `Vue.compile` → `import { compile } from 'vue'` (full build only)

`Vue.set` / `Vue.delete` are no longer needed with proxy-based reactivity and are only present in compat build.

## In plugins

Plugins must import these APIs instead of receiving `Vue`:

```js
// Vue 3 plugin
import { nextTick } from 'vue'

const plugin = {
  install(app) {
    nextTick(() => { /* ... */ })
  }
}
```

Ensure Vue is externalized in the plugin’s bundler config so it is not bundled.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/global-api-treeshaking.html
- sources/vue-migration/src/breaking-changes/global-api-treeshaking.md
-->
