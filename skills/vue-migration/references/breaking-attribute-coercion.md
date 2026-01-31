---
name: vue-migration-attribute-coercion
description: Vue 3 attribute coercion - false no longer removes attribute; use null/undefined.
---

# Attribute Coercion

Low-level change; most code unaffected.

- **Boolean `false`:** Vue 3 no longer **removes** the attribute; it sets `attr="false"`. To remove the attribute, bind **`null`** or **`undefined`**.
- **Enumerated attributes** (e.g. `contenteditable`, `draggable`, `spellcheck`) are treated like normal non-boolean attributes; no special coercion.

## Migration

```html
<!-- Vue 2: false could remove attribute -->
<div :hidden="false"></div>
<!-- no hidden attribute -->

<!-- Vue 3: false outputs attr="false" -->
<div :hidden="false"></div>
<!-- hidden="false" -->

<!-- To remove: use null or undefined -->
<div :hidden="shouldHide ?? undefined"></div>
```

Useful for `aria-*` and similar: use `null`/`undefined` when the attribute should be absent.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/attribute-coercion.html
- sources/vue-migration/src/breaking-changes/attribute-coercion.md
-->
