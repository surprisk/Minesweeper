<template>
  <header>
    <SvgBomb id="svg_bomb_header"/>
    <h1>Minesweeper</h1>
    <BtnToggle id="toggle_darkmode" @isChecked="v => $emit('darkmode', v)"/>
  </header>
</template>

<script>
import BtnToggle from './form/BtnToggle.vue'
import SvgBomb from './svg/SvgBomb.vue'

export default {
  name: 'MsHeader',
  components: {
    SvgBomb,
    BtnToggle
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  header{
    display: flex;
    align-items: center;
    justify-content: center;
    gap: .2em;
    padding: 2em;
  }

  #svg_bomb_header{
    width: 2em;
  }

  #toggle_darkmode{
    position: absolute;
    right: 4em;
    top: 2em;
  }
</style>
