<template>
    <div :id="caseId" class="case" @click.once="$emit('caseClicked', casePosition)">
      <slot></slot>
    </div>
</template>

<script>
export default {
  name: 'MsCase',
  props: ['casePosition'],
  computed: {
    caseId() {
      return `r${this.casePosition.row}c${this.casePosition.column}`
    }
  }

}
</script>

<style scoped>
  div{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 4em;
    width: 4em;
    border-radius: .3em;
    background-color: var(--item)
  }

  span{
    display: inline-block;
    font-size: 2em;
  }
</style>
