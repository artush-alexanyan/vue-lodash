<template>
  <div class="about">
    <div class="container">
      <div class="h4 text-center text-info">About Page</div>
      <button class="btn btn-success mt-3 mr-3" @click="test">Test lodash</button>
      <button class="btn btn-danger mt-3" @click="debounceMethod">Test debounce</button>
      <p class="text-danger mt-1">See the console!</p>
    </div>
  </div>
</template>

<script>
// import _ from 'lodash'
export default {
  name: 'About',
  methods: {
    test() {
      console.log(this.lodash.random(20))
      console.log(this._.random(20))
      console.log(this.custom.random(20))
    },
    debounceMethod () {
      console.log(this._.debounce (function () {
        console.log('Hello debounse')
      },5000))
    }
      
  }
}
</script>

<style scoped>

</style>