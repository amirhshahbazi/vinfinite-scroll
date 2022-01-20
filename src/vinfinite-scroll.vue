<script>

export default /*#__PURE__*/{
  name: 'VinfiniteScroll',
  data() {
    return {
      observer: null,
    }
  },
  mounted() {
    this.observer = new IntersectionObserver(([entry]) => {
      this.observerChanged(entry)
    })
    this.observer.observe(this.$el)
  },
  methods: {
    observerChanged(entry) {
      if (entry && entry.isIntersecting) {
        this.$emit('notifyEndReached')
      }
    }
  },
  destroyed() {
    this.observer.disconnect()
  }
};
</script>

<template>
  <div class="vinfinite-scroll">
  </div>
</template>
