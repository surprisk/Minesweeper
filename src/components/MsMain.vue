<template>
  <button @click="test">aaa</button>
</template>

<script>
export default {
  name: 'MsMain',
  data() {
    return {}
  },
  methods:{
    test() {
      console.log('hello world')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
