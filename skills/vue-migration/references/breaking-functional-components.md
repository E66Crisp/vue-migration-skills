---
name: vue-migration-functional-components
description: Vue 3 functional components are plain functions; SFC functional removed.
---

# Functional Components

- **Functional components** in Vue 3 are **plain functions** receiving `(props, context)`. No `{ functional: true }` option.
- **SFC:** `<template functional>` and the `functional` option are **removed**. Use a normal stateful component; performance difference is negligible.

## Migration (render function)

```js
// Vue 2
export default {
  functional: true,
  props: ['level'],
  render(h, { props, data, children }) {
    return h(`h${props.level}`, data, children)
  }
}

// Vue 3
import { h } from 'vue'

const DynamicHeading = (props, context) => {
  return h(`h${props.level}`, context.attrs, context.slots.default?.())
}
DynamicHeading.props = ['level']
export default DynamicHeading
```

`context` has `attrs`, `slots`, `emit`.

## Migration (SFC)

Remove `functional` and use `$props` / `$attrs` in template:

```vue
<!-- Vue 2 -->
<template functional>
  <component :is="`h${props.level}`" v-bind="attrs" v-on="listeners" />
</template>

<!-- Vue 3 -->
<template>
  <component :is="`h${$props.level}`" v-bind="$attrs" />
</template>
```

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/functional-components.html
- sources/vue-migration/src/breaking-changes/functional-components.md
-->
