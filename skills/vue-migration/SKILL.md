---
name: vue-migration
description: Vue 2 to Vue 3 migration - breaking changes, migration build, and ecosystem recommendations. Use when upgrading Vue 2 apps or libraries to Vue 3, or when answering migration-related questions.
---

> Skill based on Vue 3 Migration Guide (v3-migration.vuejs.org), generated 2026-02-01.

Skills for migrating Vue 2 applications and libraries to Vue 3: migration build workflow, global API changes, breaking changes (template, components, render, directives, lifecycle), and new features and recommendations.

## Core References

| Topic | Description | Reference |
|-------|-------------|-----------|
| Migration Build | @vue/compat setup, compat config, upgrade workflow | [core-migration-build](references/core-migration-build.md) |
| Global API | createApp, app instance, config, prototype, extend | [core-global-api](references/core-global-api.md) |
| Global API Treeshaking | Named exports (nextTick, reactive, etc.) | [core-global-api-treeshaking](references/core-global-api-treeshaking.md) |

## Breaking Changes

### Template & Directives

| Topic | Description | Reference |
|-------|-------------|-----------|
| v-model | modelValue/update:modelValue, .sync → v-model:arg | [breaking-v-model](references/breaking-v-model.md) |
| key | v-if branches, template v-for key placement | [breaking-key-attribute](references/breaking-key-attribute.md) |
| v-if vs v-for | Precedence change (v-if wins in Vue 3) | [breaking-v-if-v-for](references/breaking-v-if-v-for.md) |
| v-bind | Merge order (object vs individual attribute) | [breaking-v-bind](references/breaking-v-bind.md) |
| v-on.native | Modifier removed; use emits option | [breaking-v-on-native-modifier-removed](references/breaking-v-on-native-modifier-removed.md) |
| Transition | Class names v-enter/v-leave → v-enter-from/v-leave-from | [breaking-transition](references/breaking-transition.md) |
| TransitionGroup | No default root; use tag attribute | [breaking-transition-group](references/breaking-transition-group.md) |
| Attribute coercion | false no longer removes attribute | [breaking-attribute-coercion](references/breaking-attribute-coercion.md) |
| KeyCode modifiers | Removed; use kebab-case key names | [breaking-keycode-modifiers](references/breaking-keycode-modifiers.md) |

### Components & Options

| Topic | Description | Reference |
|-------|-------------|-----------|
| Filters | Removed; use methods or computed | [breaking-filters](references/breaking-filters.md) |
| data option | Must be function; mixin merge shallow | [breaking-data-option](references/breaking-data-option.md) |
| emits option | Declare component events | [breaking-emits-option](references/breaking-emits-option.md) |
| Async components | defineAsyncComponent, loader option | [breaking-async-components](references/breaking-async-components.md) |
| Functional components | Plain function only; SFC functional removed | [breaking-functional-components](references/breaking-functional-components.md) |

### Render & Slots & Attrs

| Topic | Description | Reference |
|-------|-------------|-----------|
| Render function API | h import, flat VNode props, resolveComponent | [breaking-render-function-api](references/breaking-render-function-api.md) |
| Slots unification | $scopedSlots removed; $slots as functions | [breaking-slots-unification](references/breaking-slots-unification.md) |
| $listeners removed | Merged into $attrs | [breaking-listeners-removed](references/breaking-listeners-removed.md) |
| $attrs class/style | $attrs now includes class and style | [breaking-attrs-includes-class-style](references/breaking-attrs-includes-class-style.md) |

### Directives & Instance & Lifecycle

| Topic | Description | Reference |
|-------|-------------|-----------|
| Custom directives | Hook names (bind→beforeMount, etc.) | [breaking-custom-directives](references/breaking-custom-directives.md) |
| Mount behavior | App appended inside target, not replacing | [breaking-mount-changes](references/breaking-mount-changes.md) |
| $children removed | Use template refs | [breaking-children-removed](references/breaking-children-removed.md) |
| Events API | $on, $off, $once removed; use event bus lib | [breaking-events-api](references/breaking-events-api.md) |
| watch on arrays | Trigger on replacement only unless deep | [breaking-watch](references/breaking-watch.md) |

## New & Recommendations

| Topic | Description | Reference |
|-------|-------------|-----------|
| Fragments | Multiple root nodes; $attrs distribution | [new-fragments](references/new-fragments.md) |
| Recommendations | Vite, Pinia, Volar, Vue Router 4, etc. | [recommendations](references/recommendations.md) |
