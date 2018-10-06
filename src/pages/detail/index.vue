<template>
  <web-view :src="url"></web-view>
</template>

<script>
export default {
  data () {
    return {
      url: ''
    }
  },

  methods: {
  },

  onLoad (options) {
    console.log(options)
    this.url = options.url
  }
}
</script>

<style scoped>
</style>
