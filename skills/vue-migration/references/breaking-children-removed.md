---
name: vue-migration-children-removed
description: Vue 3 removes $children; use template refs to access child instances.
---

# $children Removed

**`$children`** is removed in Vue 3. Use **template refs** to access child component instances when needed.

## Migration

```js
// Vue 2
mounted() {
  console.log(this.$children) // [VueComponent]
}

// Vue 3: use ref on the child component
// Template: <my-button ref="btnRef" />
// setup() or options: this.$refs.btnRef
```

Prefer refs (and possibly expose() in Composition API) over relying on direct child collection.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/children.html
- sources/vue-migration/src/breaking-changes/children.md
-->
