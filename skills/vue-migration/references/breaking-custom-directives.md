---
name: vue-migration-custom-directives
description: Vue 3 custom directive hooks renamed to align with component lifecycle.
---

# Custom Directive Hooks

Directive hook names in Vue 3 align with component lifecycle. `binding.expression` is removed.

## Hook mapping

| Vue 2     | Vue 3         |
|-----------|----------------|
| bind      | beforeMount    |
| inserted  | mounted        |
| update    | (removed; use updated) |
| componentUpdated | updated   |
| unbind    | unmounted      |

**New:** `created`, `beforeUpdate`, `beforeUnmount`.

## Migration

```js
// Vue 2
Vue.directive('highlight', {
  bind(el, binding, vnode) {
    el.style.background = binding.value
  }
})

// Vue 3
app.directive('highlight', {
  beforeMount(el, binding, vnode) {
    el.style.background = binding.value
  }
})
```

**Instance access:** In Vue 2 use `vnode.context`; in Vue 3 use `binding.instance`. On multi-root (fragment) components, directives are ignored and a warning is logged.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/custom-directives.html
- sources/vue-migration/src/breaking-changes/custom-directives.md
-->
