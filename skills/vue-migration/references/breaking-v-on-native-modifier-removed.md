---
name: vue-migration-v-on-native-modifier-removed
description: Vue 3 removes .native modifier; use emits option for component events.
---

# v-on.native Modifier Removed

The **`.native`** modifier is removed in Vue 3. Listeners that are **not** declared in the child’s **`emits`** are applied to the root element as native listeners.

## Migration

```html
<!-- Vue 2 -->
<my-component
  v-on:close="handleComponentEvent"
  v-on:click.native="handleNativeClickEvent"
/>

<!-- Vue 3: drop .native; declare emitted events in child -->
<my-component
  v-on:close="handleComponentEvent"
  v-on:click="handleNativeClickEvent"
/>
```

In the child, declare only **component** events in `emits`; e.g. `emits: ['close']`. Then `close` is treated as an emit, and `click` is applied to the root as a native listener.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/v-on-native-modifier-removed.html
- sources/vue-migration/src/breaking-changes/v-on-native-modifier-removed.md
-->
