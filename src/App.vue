<template>
  <div id="app">
    {{ message }}
  </div>
</template>

<script>
const mydata = require('./data.json')

export default {
  name: 'app',
  data () {
    return {
      message: mydata
    }
  }
}
</script>

<style lang="scss">
</style>
