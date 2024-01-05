<template>
  <div class='btn-toggle'>
    <label>
      <input type='checkbox' v-model="isChecked" @click="$emit('isChecked', isChecked)">
      <span></span>
    </label>
  </div>
</template>

<script>
export default {
  name: 'BtnToggle',
  data() {
    return {
      isChecked: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn-toggle{
  --toggle-size: 4em;
}
.btn-toggle{
  position: relative;
  width: var(--toggle-size);
  --light: var(--item-light);
  --dark: var(--item-dark);
}

label {
  position: absolute;
  width: 100%;
  height: calc(var(--toggle-size)/2);
  background-color: var(--dark);
  border-radius: calc(var(--toggle-size)/4);
  cursor: pointer;
}

input {
  position: absolute;
  display: none;
}

span {
  position: absolute;
  left: -0.1em;
  width: calc(100% + 0.2em);
  height: calc(var(--toggle-size)/2);
  border-radius: calc(var(--toggle-size)/4);
  transition: 0.3s;
}

input:checked ~ span {
  background-color: var(--light);
}

span::before {
  content: "";
  position: absolute;
  top: calc(var(--toggle-size)*0.08);
  left: calc(var(--toggle-size)*0.12);
  width: calc(var(--toggle-size)/3);
  height: calc(var(--toggle-size)/3);
  border-radius: 50%;
  box-shadow: inset calc(var(--toggle-size)/8) calc(var(--toggle-size)*0.04) 0px 0px var(--light);
  background-color: var(--dark);
  transition: 0.3s;
}

input:checked ~ span::before {
  transform: translateX(calc(var(--toggle-size)/2));
  background-color: var(--dark);
  box-shadow: none;
}
</style>
