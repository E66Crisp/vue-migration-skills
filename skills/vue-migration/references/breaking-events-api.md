---
name: vue-migration-events-api
description: Vue 3 removes $on, $off, $once; use external event bus or provide/inject.
---

# Events API ($on, $off, $once) Removed

Vue 3 **removes** instance methods **`$on`**, **`$off`**, and **`$once`**. Instances are no longer event emitters.

## Migration (event bus)

Replace a Vue 2 event bus with a small external emitter (e.g. mitt, tiny-emitter) or `provide`/`inject`:

```js
// eventBus.js (Vue 3)
import mitt from 'mitt'
export const eventBus = mitt()
```

```js
// Usage: eventBus.emit('event'), eventBus.on('event', fn), eventBus.off('event', fn)
```

Or provide the bus from the app and inject it where needed.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/events-api.html
- sources/vue-migration/src/breaking-changes/events-api.md
-->
