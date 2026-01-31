---
name: vue-migration-transition
description: Vue 3 transition class names v-enter/v-leave renamed to v-enter-from/v-leave-from.
---

# Transition Class Names

Vue 3 renames transition classes for clarity:

- **`v-enter`** → **`v-enter-from`**
- **`v-leave`** → **`v-leave-from`**

Props: `enter-class` → `enter-from-class`, `leave-class` → `leave-from-class` (in JS: `enterFromClass`, `leaveFromClass`).

## Migration

```css
/* Vue 2 */
.v-enter, .v-leave-to { opacity: 0; }
.v-leave, .v-enter-to { opacity: 1; }

/* Vue 3 */
.v-enter-from, .v-leave-to { opacity: 0; }
.v-leave-from, .v-enter-to { opacity: 1; }
```

Do a project-wide search for `.*-enter` and `.*-leave` and update to `-enter-from` / `-leave-from` where applicable.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/transition.html
- sources/vue-migration/src/breaking-changes/transition.md
-->
