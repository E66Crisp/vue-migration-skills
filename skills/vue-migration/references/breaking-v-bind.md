---
name: vue-migration-v-bind
description: Vue 3 v-bind object and individual attribute order determines merge result.
---

# v-bind Merge Order

In Vue 3, when an element has both **`v-bind="object"`** and an **individual attribute** for the same name, the **order of declaration** decides the final value (later overwrites). In Vue 2, the individual attribute always overwrote the object.

## Migration

```html
<!-- Vue 2: individual always wins -->
<div id="red" v-bind="{ id: 'blue' }"></div>
<!-- result: id="red" -->

<!-- Vue 3: order matters -->
<div id="red" v-bind="{ id: 'blue' }"></div>
<!-- result: id="blue" (object then id) -->

<div v-bind="{ id: 'blue' }" id="red"></div>
<!-- result: id="red" -->
```

To keep “individual overwrites object” behavior, put the individual attribute **after** `v-bind="object"`.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/v-bind.html
- sources/vue-migration/src/breaking-changes/v-bind.md
-->
