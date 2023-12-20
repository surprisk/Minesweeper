<template>
  <MsMain/>
  <BtnToggle v-model="checked"/>
  {{ checked }}
</template>

<script>
import MsMain from './components/MsMain.vue'
import BtnToggle from './components/BtnToggle.vue'

export default {
  name: 'App',
  components: {
    MsMain,
    BtnToggle
  },
  data() {
    return {
      checked: false
    }
  }
}
</script>

<style>
@import '@/assets/css/global.minesweeper.css';

:root{
    --background: black;
    --color: white;
    --border: lightgrey;
    --item: grey;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
