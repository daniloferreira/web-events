<template>

  <div>
    <button v-on:click="testingGet">
      Test the get
    </button>

    <div v-for="event in eventsResults" v-bind:key="event">
      <span>{{event}}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class TestingUiEvents extends Vue {
  eventsResults: String[] = []

  testingGet = () => {
    fetch('http://localhost:3000/testing').then(response => response.text()).then(body => this.eventsResults.push(body))
  }
}
</script>

<style scoped>

</style>
