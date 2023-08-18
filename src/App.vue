<template>
  <div :id="$style.app">
    <h1>{{ title }}</h1>
    <Button @click="increment">Click me</Button>
    <DirectivesTest />
    <StarRating />
  </div>
  
  
</template>

<script>

import DirectivesTest  from './components/DirectivesTest'
import Button from "./components/Button.vue";
import StarRating from './components/StarRating.vue';

export default {
  name: 'App',
  components: {
    Button,
    DirectivesTest,
    StarRating
  },
  data() {
    return {
      amountOfClicks: 0
    }
  },
  computed: {
    title() {
      return `Amount of clicks: ${this.amountOfClicks}`
    }
  },
  methods: {
    increment() {
      this.amountOfClicks += 1
    }
  },
}
</script>

<style module>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
