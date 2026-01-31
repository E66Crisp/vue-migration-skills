---
name: vue-migration-slots-unification
description: Vue 3 unifies slots - $scopedSlots removed, $slots exposes functions.
---

# Slots Unification

- **`$scopedSlots` removed.** All slots are on **`$slots`** and are **functions** in Vue 3.
- In render functions, slot content is passed as the third argument (object of slot name → function).

## Migration

```js
// Vue 2
this.$scopedSlots.header
this.$slots.mySlot

// Vue 3
this.$slots.header()   // call to get VNode(s)
this.$slots.mySlot()
```

Render: use the object form for slot content:

```js
// Vue 2
h(LayoutComponent, [
  h('div', { slot: 'header' }, this.header)
])

// Vue 3
h(LayoutComponent, {}, {
  header: () => h('div', this.header)
})
```

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/slots-unification.html
- sources/vue-migration/src/breaking-changes/slots-unification.md
-->
