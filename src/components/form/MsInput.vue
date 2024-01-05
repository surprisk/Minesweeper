<template>
  <div class="form-wrapper">
    <label>
      {{ label }}
    </label><br/>
    <input type="number" :value="formValue" @input="$emit('update:formValue', Number($event.target.value))">
  </div>
</template>

<script>
export default {
  name: 'MsInput',
  props: {
    label: String,
    formValue: Number
  }
}
</script>

<style scoped>
  .form-wrapper{
    display: inline-block;
    text-align: left;
    margin: .4em;
  }

  label{
    display: inline-block;
    font-size: 1.5em;
    margin-bottom: .2em;
  }

  input{
    display: inline-block;
    padding: .3em .2em;
    border-radius: .2em;
    border: .15em solid var(--border);
    background-color: var(--item);
    color: var(--color)
  }
</style>
