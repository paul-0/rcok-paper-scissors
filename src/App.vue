<template>
  <div id="top">
    <h1 v-if="modeClassic">{{ $t('title') }}</h1>
    <h3 v-else>{{ $t('title-sheldon') }}</h3>
    <div id="score">
      {{ $t('score') }}
      <div>{{ score }}</div>
    </div>
  </div>
  <GameComponent id="content" :add-score="addScore" :mode-classic="modeClassic" />
  <div id="div-buttons">
    <button id="button-rules" @click="showRules^=true">{{ $t('rules') }}</button>
    <button id="button-mode" @click="changeMode">{{ modeClassic? $t('mode-classic'):$t('mode-sheldon') }}</button>
    <button id="change-locale" @click="changeLocale">{{ $t('language')+this.$i18n.locale}}</button>
  </div>
  <RulesComponent v-show="showRules" :mode-classic="modeClassic"
                  :close-callback="() => {this.showRules=false}"></RulesComponent>
  <div class="attribution">
    {{ $t('challenge-by') }} <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
    {{ $t('coded-by') }} <a href="https://github.com/paul-0">Paul Devilliers</a>.
  </div>
</template>

<script>
import GameComponent from "@/components/Game";
import RulesComponent from "@/components/Rules";
export default {
  name: 'App',
  data() {
    return {
      score: parseInt(localStorage.getItem('score')) || 0,
      showRules: false,
      modeClassic: true
    }
  },
  components: {
    RulesComponent,
    GameComponent
  },
  methods: {
    addScore(score) {
      this.score += score;
      localStorage.setItem('score', this.score.toString());
    },
    changeMode() {
      this.modeClassic = !this.modeClassic;
    },
    changeLocale() {
      this.$i18n.locale = this.$i18n.locale === 'en' ? 'fr' : 'en';
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed:ital,wght@0,400;0,500;0,700;0,800;1,500&display=swap');
@import url('https://fonts.googleapis.com/icon?family=Material+Icons');

.attribution {
  font-size: 11px; text-align: center;
  margin: 2rem;
  a {
    color: #7b8ac7;
  }
}

:root {
  background-repeat: no-repeat;
  background-size: cover;
  background-image: radial-gradient(hsl(214, 47%, 23%), hsl(237, 49%, 15%));

  --scissors: hsl(39, 89%, 49%);
  --paper:  hsl(230, 89%, 62%);
  --rock: hsl(349, 71%, 52%);
  --lizard: hsl(261, 73%, 60%);
  --spock: hsl(189, 59%, 53%);

  --transparent-gray: #80808099;
  --dark-text: hsl(229, 25%, 31%);
  --header-outline:  hsl(217, 16%, 45%);
}

:root, body, #app {
  height: 100%;
  width: 100%;
  margin: 0;
  min-width: 300px;
}

#app {
  font-family: 'Barlow Semi Condensed', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  display: flex;
  flex-direction: column;

  #div-buttons {
    position: absolute;
    right: 2rem;
    bottom: 4rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.5rem;

    button {
      background: none;
      border: medium solid var(--transparent-gray);
      color: var(--transparent-gray);
      border-radius: 100px;
      width: max-content;
      padding: 5px 20px;
      font-weight: bold;
      cursor: pointer;
    }
  }

}

#content {
  flex-grow: 1;
}

#top {
  margin: 2rem auto;
  display: flex;
  align-items: center;
  width: 40%;
  border: solid gray;
  border-radius: 1rem;
  padding: 0 1rem;

  h1,h2,h3 {
    font-weight: bolder;
    width: min-content;
    margin-right: auto;
    margin-left: 0;
    text-align: left;
  }

  #score {
    border-radius: 0.5rem;
    width: 5rem;
    height: 5rem;
    background-color: white;
    color: hsl(229, 64%, 46%);
    margin-right: 2rem;
    div {
      font-size: xxx-large;
      font-weight: bolder;
      color: var(--dark-text);
    }
  }
}

@media (max-width: 600px) {
  #top {
    width: 60%;
    font-size: xx-small;
    margin: 1rem auto;

    #score {
      font-size: small;
      padding-top: 3px;
      margin-right: 1rem;
      height: 3rem;
      width: 3rem;
      div {
        font-size: x-large;
      }
    }
  }

  #div-buttons {
    margin: auto;
    position: static !important;
  }
  .attribution {
    margin: 0.7rem auto;
  }
}
</style>