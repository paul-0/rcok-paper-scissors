<template>
  <div id="root">
    <div id="play-component">
      <img id="triangle" src="../assets/images/bg-triangle.svg" alt="">
      <MoveComponent v-bind:move="'paper'" v-on:click="play('paper')"/>
      <MoveComponent move="scissors" v-on:click="play('scissors')"/>
      <MoveComponent move="rock" v-on:click="play('rock')"/>
    </div>
  </div>
</template>

<script>
import MoveComponent from "@/components/MoveComponent";
export default {
  name: "PlayComponent",
  components: {MoveComponent},
  props: {
    play: Function
  },
}
</script>

<style scoped lang="scss">
#root {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

#play-component {
  display: flex;
  justify-content: center;
  align-items: center;
  height: max-content;
  width: max-content;
  margin: auto;
  position: relative;
}

#triangle {
  height: 50%;
}
.move {
  position: absolute;
  background-color: white;
  border-radius: 100%;
  height: 8rem;
  width: 8rem;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  border: 1.2rem solid;
  &:hover {
    filter: brightness(0.8);
  }
}
#paper {
  left: -25%;
  top: -25%;
}
#scissors {
  right: -25%;
  top: -25%;
}
#rock {
  bottom: -25%;
}

@media (max-width: 600px){
  #triangle {
    height: 180px;
  }
}
</style>