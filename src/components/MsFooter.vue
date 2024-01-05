<template>
    <footer><SvgLogo/> Crafted by Pievie team</footer>
</template>

<script>
import SvgLogo from './svg/SvgLogo.vue';

export default {
  name: 'MsFooter',
  components: {
    SvgLogo
  }
}
</script>

<style scoped>
  footer{
    display: flex;
    justify-content: center;
    gap: .2em;
    padding: 2em;
  }
</style>
