---
name: vue-migration-watch
description: Vue 3 watch on arrays only triggers on replacement unless deep option is used.
---

# watch on Arrays

In Vue 3, **watching an array** triggers the callback only when the **array is replaced**, not on in-place mutation. Use the **`deep`** option to react to mutations.

## Migration

```js
// Vue 2: handler could run on array mutation
watch: {
  bookList(val, oldVal) {
    console.log('book list changed')
  }
}

// Vue 3: for mutation, add deep
watch: {
  bookList: {
    handler(val, oldVal) {
      console.log('book list changed')
    },
    deep: 1  // Vue 3.5+: array replacement + mutation
    // deep: true  // Vue 3.0–3.4: also deep object changes
  }
}
```

Vue 3.5+ supports `deep: 1` for array replacement and mutation without deep object traversal.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/watch.html
- sources/vue-migration/src/breaking-changes/watch.md
-->
