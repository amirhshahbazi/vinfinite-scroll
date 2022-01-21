<p align="center">
    <img width="150" src="https://jsdev.best/vinfinite-scroll.png" alt="Vinfinite Scroll">
</p>

# Vinfinite Scroll

> Infinite scroll component for Vue.js
- 🟩 Easy to use
- 🟩 SSR compatible

Vinfinite Scroll currently works with Vue 2.

---

## Installation

```bash
yarn add @amirhshahbazi/vinfinite-scroll
# or using npm:
npm i @amirhshahbazi/vinfinite-scroll
```

---

## Usage

### Import the component
```js
import VinfiniteScroll from "@amirhshahbazi/vinfinite-scroll"
```

### Add the component to the end of the list you want to use
Every time the scroll position reaches `vinfinite-scroll`, the `notifyEndReached` is invoked.
```js
  <div class="list">
    <div v-for="(item) in list" :key="item">
      {{ item }}
    </div>
    <vinfinite-scroll @notifyEndReached="notify"></vinfinite-scroll>
  </div>
```

### Add data to the previous list whenever scroll is reached
```js
  methods: {
    notify() {
      // fetch the rest of the data and add it to the list
    }
  }
```

## Complete example

```js
<template>
  <div class="list">
    <div v-for="(item) in list" :key="item">
      {{ item }}
    </div>
    <vinfinite-scroll @notifyEndReached="notify"></vinfinite-scroll>
  </div>
</template>

<script>
import VinfiniteScroll from "@amirhshahbazi/vinfinite-scroll"

export default {
  name: 'App',
  data() {
    return {
      list: []
    }
  },
  components: {
    'vinfinite-scroll': VinfiniteScroll
  },
  mounted() {
    // populate the list with some items
    this.list = Array.from({length: 100}, (v, k) => k + 1)
  },
  methods: {
    notify() {
      // fetch the rest of the data and add it to the list
      this.list = this.list.concat(Array.from({length: 100}, (v, k) => k + 1 + this.list.length))
    }
  }
}
</script>

```

---

## Use with Nuxt
Inside `plugins/vinfinite-scroll.js`:
```js
import Vue from 'vue'
import VinfiniteScroll from '@amirhshahbazi/vinfinite-scroll'

Vue.use(VinfiniteScroll)
```

In the pages or components:
```vue
<vinfinite-scroll @notifyEndReached="notify" />
```

---

## License

[MIT](http://opensource.org/licenses/MIT)
