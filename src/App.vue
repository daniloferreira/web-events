<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <TestingUiEvents></TestingUiEvents>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import HelloWorld from './components/HelloWorld.vue'
import TestingUiEvents from './components/TestingUiEvents.vue'

@Component({
  components: {
    TestingUiEvents,
    HelloWorld
  }
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
