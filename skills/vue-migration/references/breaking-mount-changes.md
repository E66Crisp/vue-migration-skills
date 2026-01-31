---
name: vue-migration-mount-changes
description: Vue 3 mount appends inside target element instead of replacing it.
---

# Mount API Behavior

In Vue 2, mounting an app **replaced** the mount target element with the app’s root. In Vue 3, the app’s root is **appended as a child** of the mount target; the target’s `innerHTML` is replaced but the target element itself remains.

## Resulting DOM

```html
<!-- Mount target: <div id="app">...</div> -->

<!-- Vue 2: target replaced -->
<body>
  <div id="rendered">Hello Vue!</div>
</body>

<!-- Vue 3: target kept, app inside -->
<body>
  <div id="app" data-v-app="">
    <div id="rendered">Hello Vue!</div>
  </div>
</body>
```

Do not rely on the mount element being replaced. Use the app root’s element for styling or selectors.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/mount-changes.html
- sources/vue-migration/src/breaking-changes/mount-changes.md
-->
