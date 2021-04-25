<template>
  <div>
    <Magnet
      v-for="(word, index) in randWords"
      :key="'word-' + index"
      :word="word"
    />
  </div>
</template>

<script>
import { words } from "./assets/words.js";
import Magnet from "./components/Magnet.vue";

export default {
  name: "App",
  components: {
    Magnet,
  },
  computed: {
    randWords() {
      const magnets = ["Salmon", "Addyson"];

      // grab random 100 words
      for (let i = 0; i < 100; i++) {
        magnets.push(words[Math.floor(Math.random() * 3000)]);
      }

      return magnets;
    },
  },
};
</script>

<style>
html,
body {
  height: 100%;
  margin: 0;
  font-family: "Open Sans", sans-serif;
}

html {
  font-size: 62.5%;
}

body {
  font-size: 1.4rem;
}

h1 {
  font-size: 2.4rem;
  margin: 0;
  padding: 1rem;
}

h2 {
  font-size: 2rem;
  margin: 0;
  padding: 1rem;
}

h3 {
  font-size: 1.8rem;
  margin: 0;
  padding: 1rem;
}

h4 {
  font-size: 1.6rem;
  margin: 0;
  padding: 1rem;
}

p {
  padding-left: 1rem;
  padding-right: 1rem;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  height: 100%;
  width: 100%;
  background-color: #131313;
}
</style>
