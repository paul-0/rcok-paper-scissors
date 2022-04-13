<template>
  <div>
    <PlayComponent v-show="!endGame" v-bind:play="play"></PlayComponent>
    <EndComponent v-bind:player-move="playerMove" v-bind:house-move="houseMove"
                  v-show="endGame"></EndComponent>
  </div>
</template>

<script>
import PlayComponent from "@/components/PlayComponent";
import EndComponent from "@/components/EndComponent";

export default {
  name: "Game-component",
  components: {
    PlayComponent, EndComponent
  },
  data () {
    return {
      endGame: false,
      playerMove: "",
      houseMove: ""
    }
  },
  methods: {
    play(move) {
      this.playerMove = move;
      this.houseMove = ["rock", "paper", "scissors"][Math.floor(Math.random() * 3)];
      this.endGame = true;
    }
  }
}
</script>

<style scoped>
div {

}
</style>