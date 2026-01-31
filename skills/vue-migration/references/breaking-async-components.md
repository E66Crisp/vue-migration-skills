---
name: vue-migration-async-components
description: Vue 3 async components use defineAsyncComponent; loader option, no resolve/reject.
---

# Async Components

Vue 3 requires **`defineAsyncComponent`** for async components. The factory no longer receives `resolve`/`reject`; it must return a Promise.

## Migration

```js
// Vue 2
const asyncModal = () => import('./Modal.vue')
const asyncModalWithOptions = {
  component: () => import('./Modal.vue'),
  delay: 200,
  timeout: 3000,
  error: ErrorComponent,
  loading: LoadingComponent
}

// Vue 3
import { defineAsyncComponent } from 'vue'

const asyncModal = defineAsyncComponent(() => import('./Modal.vue'))

const asyncModalWithOptions = defineAsyncComponent({
  loader: () => import('./Modal.vue'),
  delay: 200,
  timeout: 3000,
  errorComponent: ErrorComponent,
  loadingComponent: LoadingComponent
})
```

- **`component`** option renamed to **`loader`**.
- Loader must **return a Promise**; it does not receive `(resolve, reject)`.

For route-level lazy loading, use Vue Router’s mechanism, not `defineAsyncComponent`.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/async-components.html
- sources/vue-migration/src/breaking-changes/async-components.md
-->
