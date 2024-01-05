<template>
  <div id='theme_wrapper'>
    <MsHeader @darkmode="v => this.theme = v ? 'dark' : 'light'"/>
    <MsMain/>
    <MsFooter/>
  </div>
</template>

<script>
import MsHeader from './components/MsHeader.vue'
import MsMain from './components/MsMain.vue'
import MsFooter from './components/MsFooter.vue'

export default {
  name: 'App',
  components: {
    MsHeader,
    MsMain,
    MsFooter
  },
  data() {
    return {
      theme: 'light',
      colore: "red",
      themes: {
        dark: {
          background: "#181818",
          color: '#ffffff',
          border: '#aaaaaa',
          item: '#3d3d3d'
        },
        light: {
          background: "#fafafa",
          color: '#484b6a',
          border: '#9394a5',
          item: '#e4e5f1'
        }
      }
    }
  },
  methods: {
    updateTheme(isChecked) {
      this.theme = isChecked ? 'dark' : 'light';
    }
  }
}

</script>

<style>
@import '@/assets/css/global.minesweeper.css';

#theme_wrapper{
    --background: v-bind('themes[theme].background');
    --color: v-bind('themes[theme].color');
    --border: v-bind('themes[theme].border');
    --item: v-bind('themes[theme].item');
    --item-dark: v-bind('themes.dark.item');
    --item-light: v-bind('themes.light.item');
}

#theme_wrapper{
  background-color: var(--background);
  color: var(--color);
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, Ubuntu;
  text-align: center;
}
</style>
