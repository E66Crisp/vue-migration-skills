---
name: vue-migration-listeners-removed
description: Vue 3 merges $listeners into $attrs; use v-bind="$attrs" only.
---

# $listeners Removed

In Vue 3, event listeners are part of **`$attrs`** (prefixed with `on` in the virtual DOM). **`$listeners`** is removed.

## Migration

```vue
<!-- Vue 2 -->
<template>
  <label>
    <input type="text" v-bind="$attrs" v-on="$listeners" />
  </label>
</template>

<!-- Vue 3 -->
<template>
  <label>
    <input type="text" v-bind="$attrs" />
  </label>
</template>
```

`$attrs` now includes both attributes and listeners (e.g. `onClose`). Use `inheritAttrs: false` and a single `v-bind="$attrs"` where you want them applied.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/listeners-removed.html
- sources/vue-migration/src/breaking-changes/listeners-removed.md
-->
