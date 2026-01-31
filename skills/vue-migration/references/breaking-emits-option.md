---
name: vue-migration-emits-option
description: Declare component events with emits option in Vue 3; required for correct attrs and .native replacement.
---

# emits Option

Vue 3 supports an **`emits`** option (like `props`) to declare which events a component emits. Declaring `emits` is recommended and affects attribute fallthrough and `.native` replacement.

## Usage

```js
export default {
  props: ['text'],
  emits: ['accepted', 'close']
}
```

Object form supports validation: `emits: { accepted: (payload) => !!payload }`.

## Why declare emits

- **`.native` removed:** listeners for non-declared events are applied to the root element as native listeners. If the component also `$emit`s that event, the parent would get it twice unless the event is declared.
- **`$attrs`:** only listeners for **declared** emits are excluded from `$attrs`; undeclared ones stay in `$attrs` and fall through.

**Re-emitting native events:** either declare the event (`emits: ['click']`) so the parent gets one logical event, or stop re-emitting and let the parent listen on the root (no `.native` in Vue 3).

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/emits-option.html
- sources/vue-migration/src/breaking-changes/emits-option.md
-->
