---
name: vue-migration-recommendations
description: Vue 3 ecosystem recommendations - Vite, Pinia, Volar, Vue Router 4, etc.
---

# New Framework-level Recommendations

Vue 3 ecosystem defaults and recommended tooling:

| Area | Vue 2 | Vue 3 |
|------|------|--------|
| Build | Vue CLI | **Vite** |
| State | Vuex | **Pinia** |
| IDE | Vetur | **Volar** |
| Router | Vue Router 3 | **Vue Router 4** |
| SSG | VuePress | **VitePress** |
| JSX | @vue/babel-preset-jsx | **@vue/babel-plugin-jsx** |
| TypeScript CLI | - | **vue-tsc** |

## Practical notes

- **Vite:** Use `create-vue` (`npm init vue@3`) for new projects. Vue CLI is in maintenance; migrate to Vite when upgrading.
- **Pinia:** Recommended over Vuex 4 for new apps; Vuex 4 still works with Vue 3 (plugin install change only).
- **Volar:** Disable Vetur when using Volar to avoid conflicts.
- **Vue Router 4:** Has its own migration guide; `<router-view>` with `<transition>`/`<keep-alive>` uses scoped-slot syntax in v4.
- **DevTools:** Use v6+ for Vue 2 and Vue 3.

<!--
Source references:
- https://v3-migration.vuejs.org/recommendations.html
- sources/vue-migration/src/recommendations.md
-->
