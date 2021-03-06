<template>
  <main>{{ headers }}</main>
</template>

<script>
export default {
  data() {
    return {
      headers: undefined
    }
  },
  async asyncData({ $axios }) {
    return {
      headers: (await $axios.$get('http://httpbin.org/headers')).headers
    }
  }
}
</script>

<style scoped>
main {
  margin: 2em;
  white-space: pre-wrap;
  line-height: 1.5em;
}
</style>
