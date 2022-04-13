<template>
  <div id="div-rules">
    <div id="rules">
      <h1>RULES</h1>
      <span v-on:click="closeCallback" class="material-icons">
        close
      </span>
      <img src="../assets/images/image-rules.svg" alt="Rules">
    </div>
  </div>
</template>

<script>
export default {
  props: {
    closeCallback: Function
  },
  name: "RulesComponent"
}
</script>

<style scoped>
#div-rules {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--transparent-gray);
}

#rules {
  background-color: white;
  border-radius: 20px;
  max-width: 500px;
  width: 500px;
  height: 400px;
  margin: auto;
  color: var(--dark-text);
  position: relative;
}

h2 {
  text-align: left;
  margin-left: 4rem;
}

span{
  position: absolute;
  top: 1rem;
  right: 1rem;
  font-size: 30px;
  cursor: pointer;
}

img {
  width: auto;
  height: 300px;
}
</style>