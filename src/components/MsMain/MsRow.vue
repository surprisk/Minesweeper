<template>
    <div class="row">
      <slot></slot>
    </div>
</template>

<script>
export default {
  name: 'MsRow'
}
</script>

<style scoped>
  .row{
    display: flex;
    gap: .2em;
  }

  .row:not(:last-child){
    margin-bottom: .2em
  }
</style>
