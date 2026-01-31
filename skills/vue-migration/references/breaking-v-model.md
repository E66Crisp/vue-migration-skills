---
name: vue-migration-v-model
description: Migrate Vue 2 v-model and .sync to Vue 3 v-model and v-model:arg.
---

# v-model and .sync Migration

## Changes

- **Component v-model:** prop `value` → `modelValue`, event `input` → `update:modelValue`.
- **`.sync` removed:** use `v-model:propName` instead.
- **`model` option removed:** use `v-model:propName` on the parent.
- **New:** multiple `v-model` bindings and custom modifiers on components.

## Migration

**Default v-model:**

```html
<!-- Parent: unchanged -->
<ChildComponent v-model="pageTitle" />
```

```js
// Child: Vue 2
props: { value: String }
this.$emit('input', newValue)

// Child: Vue 3
props: { modelValue: String }
emits: ['update:modelValue']
this.$emit('update:modelValue', newValue)
```

**Replace .sync with v-model:arg:**

```html
<!-- Vue 2 -->
<ChildComponent :title.sync="pageTitle" />

<!-- Vue 3 -->
<ChildComponent v-model:title="pageTitle" />
```

Child: prop `title`, emit `update:title`. Multiple bindings: `v-model:title="..."` `v-model:content="..."`.

**Custom modifiers:** supported on component v-model; see Vue 3 docs for `modelModifiers`.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/v-model.html
- sources/vue-migration/src/breaking-changes/v-model.md
-->
