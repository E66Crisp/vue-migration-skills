---
name: vue-migration-keycode-modifiers
description: Vue 3 removes keyCode modifiers and config.keyCodes; use kebab-case key names.
---

# KeyCode Modifiers Removed

Vue 3 **removes** numeric keyCode modifiers and **`config.keyCodes`**. Use **kebab-case key names** (e.g. `page-down`, `enter`).

## Migration

```html
<!-- Vue 2 -->
<input v-on:keyup.13="submit" />
<input v-on:keyup.112="showHelp" />
<!-- with Vue.config.keyCodes.f1 = 112 -->
<input v-on:keyup.f1="showHelp" />

<!-- Vue 3: use key names -->
<input v-on:keyup.enter="submit" />
<input v-on:keyup.page-down="nextPage" />
```

Custom keys: use the kebab-case name from [KeyboardEvent.key](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key) (e.g. `PageDown` → `page-down`). `config.keyCodes` is removed.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/keycode-modifiers.html
- sources/vue-migration/src/breaking-changes/keycode-modifiers.md
-->
