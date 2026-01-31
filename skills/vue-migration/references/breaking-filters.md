---
name: vue-migration-filters
description: Replace Vue 2 filters with methods or computed properties in Vue 3.
---

# Filters Removed

Vue 3 removes filters. Use **methods** or **computed properties** instead.

## Migration

```html
<!-- Vue 2 -->
<p>{{ accountBalance | currencyUSD }}</p>
<script>
  filters: {
    currencyUSD(value) {
      return '$' + value
    }
  }
</script>

<!-- Vue 3 -->
<p>{{ accountInUSD }}</p>
<script>
  computed: {
    accountInUSD() {
      return '$' + this.accountBalance
    }
  }
</script>
```

Or call a method: `{{ formatCurrency(accountBalance) }}`.

## Global filters

Expose helpers via `app.config.globalProperties`:

```js
app.config.globalProperties.$filters = {
  currencyUSD(value) {
    return '$' + value
  }
}
```

Template: `{{ $filters.currencyUSD(accountBalance) }}`.

<!--
Source references:
- https://v3-migration.vuejs.org/breaking-changes/filters.html
- sources/vue-migration/src/breaking-changes/filters.md
-->
