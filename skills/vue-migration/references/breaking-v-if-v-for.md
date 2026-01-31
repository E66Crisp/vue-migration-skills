---
name: vue-migration-v-if-v-for
description: Vue 3 v-if has higher precedence than v-for when on same element.
---

# v-if vs v-for Precedence

In Vue 3, when **`v-if` and `v-for`** are on the **same element**, **`v-if` has higher precedence** than `v-for`. In Vue 2 it was the opposite (`v-for` won).

## Migration

Avoid using both on the same element. Prefer:

- A **computed** that filters the list, then `v-for` on the filtered list, or
- Moving `v-for` to a parent `<template>` and keeping `v-if` on the child.

```html
<!-- Avoid in Vue 3: v-if runs first, item may not exist in scope as expected -->
<div v-for="item in list" v-if="item.isVisible">{{ item.name }}</div>

<!-- Prefer: filter in computed -->
<div v-for="item in visibleList" :key="item.id">{{ item.name }}</div>
```

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/v-if-v-for.html
- sources/vue-migration/src/breaking-changes/v-if-v-for.md
-->
