---
name: vue-migration-attrs-includes-class-style
description: Vue 3 $attrs includes class and style; affects inheritAttrs false.
---

# $attrs Includes class and style

In Vue 3, **`$attrs`** includes **`class`** and **`style`** (they are no longer excluded).

## Impact

With **`inheritAttrs: false`**, you control where attributes go via `v-bind="$attrs"`. In Vue 2, `class` and `style` were still applied to the root element. In Vue 3 they are in `$attrs`, so they only go where you bind `$attrs`.

## Migration

If you use `inheritAttrs: false` and previously relied on `class`/`style` automatically on the root, ensure you either:

- Bind `$attrs` on the element that should receive them (so `class`/`style` go there), or
- Manually apply `class`/`style` where needed.

```vue
<!-- Vue 2: $attrs didn't include class/style; root still got them -->
<template>
  <label>
    <input v-bind="$attrs" />
  </label>
</template>

<!-- Vue 3: $attrs includes class/style; they go to input with v-bind="$attrs" -->
<template>
  <label>
    <input v-bind="$attrs" />
  </label>
</template>
```

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/attrs-includes-class-style.html
- sources/vue-migration/src/breaking-changes/attrs-includes-class-style.md
-->
