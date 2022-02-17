<template>
  <div>
    <Tutorial/>
    <div>count: {{ $store.state.count }}</div>
    <button @click="addCount">Add</button>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  methods: {
    addCount() {
      this.$store.dispatch('count/increment');
    },
  },
}
</script>
