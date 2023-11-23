<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">PLAY</button>
  <ReactionBlock v-if="isPlaying" :delay="delay" @end="endGame" />
  <ReactionResults v-if="showResults" :score="score" />
</template>

<script>
import ReactionBlock from "./components/ReactionBlock.vue";
import ReactionResults from "./components/ReactionResults.vue";
export default {
  name: "App",
  components: { ReactionBlock, ReactionResults },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  padding: 8px 30px;
  background-color: white;
  color: #4b7b8b;
  border: 1px solid #4b7b8b;
  border-radius: 20px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  transition: background-color 0.3s, box-shadow 0.3s;
}

button:hover {
  color: black;
}

button:disabled,
button:disabled:hover {
  color: #4b7b8b;
  cursor: not-allowed;
  background-color: white;
}
</style>
