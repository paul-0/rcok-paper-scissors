<template>
  <div>
    <PlayComponent v-show="!endGame" :play="play"></PlayComponent>
    <EndComponent :player-move="playerMove" :house-move="houseMove"
                  v-show="endGame" :reset="reset" :msg-score="msgScore"></EndComponent>
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
      houseMove: "",
      msgScore: ""
    }
  },
  props: {
    addScore: Function
  },
  methods: {
    play(move) {
      this.playerMove = move;
      this.houseMove = ["rock", "paper", "scissors"][Math.floor(Math.random() * 3)];

      let tab = ["paper", "rock", "scissors"];
      let res = tab.indexOf(this.playerMove) - tab.indexOf(this.houseMove);
      if (res === 0) {
        this.msgScore = "TIE";
      } else if (res === 1 || res === -2) {
        this.msgScore = "YOU LOSE";
        this.addScore(-1);
      } else {
        this.msgScore = "YOU WIN";
        this.addScore(1);
      }

      this.endGame = true;
    },
    reset() {
      this.endGame = false;
      this.playerMove = "";
      this.houseMove = "";
      this.msgScore = "";
    }
  }
}
</script>

<style scoped>
div {

}
</style>