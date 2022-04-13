<template>
  <div id="end-component">
    <div id="player">
      <h2>YOU PICKED</h2>
      <div class="choosen-move">
        <MoveComponent :move="playerMove" />
      </div>
    </div>
    <div id="house">
      <h2>THE HOUSE PICKED</h2>
      <div class="choosen-move">
        <MoveComponent class="house-move" :move="houseMove" />
      </div>
    </div>
  </div>
</template>

<script>
import MoveComponent from "@/components/MoveComponent";
export default {
  name: "EndComponent",
  components: {MoveComponent},
  props: {
    playerMove: {
      type: String,
      required: true
    },
    houseMove: {
      type: String,
      required: true
    }
  },
}
</script>

<style scoped lang="scss">
#end-component {
  display: flex;
  align-items: flex-start;
  gap: 2rem;
  height: 100%;
  max-width: 700px;
  margin: auto;
  * {
    flex-grow: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }
}

.choosen-move {
  background-color: var(--dark-text);
  border-radius: 100%;
  width: 10rem;
  height: 10rem;
}

.house-move {
  animation: fadeIn 3s;
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

</style>