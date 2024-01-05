<template>
    <div :id="caseId" class="case" :class="{active: isClicked}" @click.once="$emit('caseClicked', casePosition), isClicked=true" @click.right.prevent="isFlagged=!isFlagged">
      <slot v-if="isClicked"></slot>
      <SvgFlag v-if="isFlagged && !isClicked"/>
    </div>
</template>

<script>
import SvgFlag from '../svg/SvgFlag.vue';

export default {
  name: 'MsCase',
  props: ['casePosition'],
  components: {
    SvgFlag
  },
  data() {
    return {
      isClicked: false,
      isFlagged: false
    }
  },
  computed: {
    caseId() {
      return `r${this.casePosition.row}c${this.casePosition.column}`
    }
  }

}
</script>

<style scoped>
  .case{
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: .15em;
    width: 100%;
    aspect-ratio : 1 / 1;
    background-color: var(--item);
    font-size: 2em;
    position: relative;
  }

  .case:hover, .case.active{
    filter: brightness(.95);
  }
</style>
