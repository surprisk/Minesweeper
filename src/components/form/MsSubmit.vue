<template>
  <input :value="value" type="submit">
</template>

<script>
export default {
  name: 'MsSubmit',
  props: {
    value: String
  }
}
</script>

<style scoped>
  input{
    display: inline-block;
    padding: .3em .2em;
    border-radius: .2em;
    border: .15em solid var(--item);
    margin: .4em;
    background-color: var(--item);
    color: var(--color)
  }
</style>
