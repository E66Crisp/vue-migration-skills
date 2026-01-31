---
name: vue-migration-transition-group
description: Vue 3 transition-group has no default root element; use tag attribute if needed.
---

# transition-group Root Element

`<transition-group>` in Vue 3 **does not render a root element by default**. Use the **`tag`** attribute when you need a wrapper (e.g. for layout or styling).

## Migration

```html
<!-- Vue 2: default root was <span> -->
<transition-group>
  <li v-for="item in items" :key="item">{{ item }}</li>
</transition-group>

<!-- Vue 3: no root by default; add tag if you relied on it -->
<transition-group tag="ul">
  <li v-for="item in items" :key="item">{{ item }}</li>
</transition-group>
```

If styling or behavior depended on the old default `<span>`, add `tag="span"`.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/transition-group.html
- sources/vue-migration/src/breaking-changes/transition-group.md
-->
