---
name: vue-migration-data-option
description: Vue 3 data option must be a function; mixin data merge is shallow.
---

# data Option Changes

## data must be a function

Vue 3 only accepts a **function** that returns an object for `data`.

```js
// Vue 2 (root could use object)
const app = new Vue({ data: { apiKey: 'a1b2c3' } })

// Vue 3
createApp({
  data() {
    return { apiKey: 'a1b2c3' }
  }
}).mount('#app')
```

## Mixin merge is shallow

When merging `data()` from component and mixins/extends, Vue 3 merges **shallowly** (root-level only). Nested objects are no longer deep-merged.

```js
// Mixin returns { user: { name: 'Jack', id: 1 } }
// Component returns { user: { id: 2 } }

// Vue 2: merged user = { id: 2, name: 'Jack' }
// Vue 3: merged user = { id: 2 }  (component wins, no deep merge)
```

Avoid relying on deep mixin merge; refactor to explicit data or composables.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/data-option.html
- sources/vue-migration/src/breaking-changes/data-option.md
-->
