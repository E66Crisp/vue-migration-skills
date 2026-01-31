---
name: vue-migration-render-function-api
description: Vue 3 render function API - h import, flat VNode props, resolveComponent.
---

# Render Function API

Only affects code using `render()` or `h`; `<template>` users are unaffected.

## h is imported

```js
// Vue 2
export default {
  render(h) {
    return h('div')
  }
}

// Vue 3
import { h } from 'vue'
export default {
  render() {
    return h('div')
  }
}
```

## VNode props are flat

Vue 2 used nested keys (`class`, `style`, `attrs`, `domProps`, `on`). Vue 3 uses a flat object: `class`, `style`, `id`, `innerHTML`, `onClick`, etc. Merge `class`/`style` as arrays if needed: `class: ['btn', { active }]`.

## Registered components

Vue 3 VNodes are context-free; you can’t resolve components by string ID from the render context. Use `resolveComponent`:

```js
import { h, resolveComponent } from 'vue'

export default {
  setup() {
    const ButtonCounter = resolveComponent('button-counter')
    return () => h(ButtonCounter)
  }
}
```

Library authors: keep `import { h } from 'vue'` and externalize Vue in the build.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/render-function-api.html
- sources/vue-migration/src/breaking-changes/render-function-api.md
-->
