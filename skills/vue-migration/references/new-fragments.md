---
name: vue-migration-fragments
description: Vue 3 supports multiple root nodes (fragments); explicit $attrs distribution.
---

# Fragments (Multiple Root Nodes)

Vue 3 supports **multiple root nodes** in a component template. You must **explicitly** decide where `$attrs` (and class/style) are applied.

## Usage

```vue
<!-- Vue 2: single root required -->
<template>
  <div>
    <header>...</header>
    <main>...</main>
    <footer>...</footer>
  </div>
</template>

<!-- Vue 3: multiple roots; bind $attrs where fallthrough should go -->
<template>
  <header>...</header>
  <main v-bind="$attrs">...</main>
  <footer>...</footer>
</template>
```

If you don’t bind `$attrs`, they will apply to the first element (Vue 3 fallthrough). Prefer binding `v-bind="$attrs"` on the single element that should receive them (e.g. main content). See Fallthrough Attributes in Vue 3 docs.

<!--
Source references:
- https://v3-migration.vuejs.org/new/fragments.html
- sources/vue-migration/src/new/fragments.md
-->
