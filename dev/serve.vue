<script>
import Vue from 'vue';
import VinfiniteScroll from '@/vinfinite-scroll.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VinfiniteScroll
  }
});
</script>

<template>
  <div id="app">
    <vinfinite-scroll />
  </div>
</template>
