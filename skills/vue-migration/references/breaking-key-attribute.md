---
name: vue-migration-key-attribute
description: Vue 3 key on v-if branches and template v-for; unique keys required.
---

# key Attribute Changes

## Conditional branches (v-if / v-else / v-else-if)

- Vue 3 **auto-generates** unique keys for branches if you don’t provide one. You can **omit** `key` on branches.
- If you **do** provide `key`, each branch must have a **unique** key. Reusing the same key to force reuse is no longer allowed.

```html
<!-- Vue 2 -->
<div v-if="condition" key="yes">Yes</div>
<div v-else key="no">No</div>

<!-- Vue 3 (preferred: no keys) -->
<div v-if="condition">Yes</div>
<div v-else>No</div>
```

## template v-for

**`key` must be on the `<template>`**, not on its children.

```html
<!-- Vue 2 -->
<template v-for="item in list">
  <div :key="'heading-' + item.id">...</div>
  <span :key="'content-' + item.id">...</span>
</template>

<!-- Vue 3 -->
<template v-for="item in list" :key="item.id">
  <div>...</div>
  <span>...</span>
</template>
```

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/key-attribute.html
- sources/vue-migration/src/breaking-changes/key-attribute.md
-->
