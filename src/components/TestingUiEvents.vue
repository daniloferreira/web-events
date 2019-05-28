<template>

  <div>
    <button v-on:click="testingGet">
      Emit event
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
    const eventBody = JSON.stringify({ 'event-type': 'click', 'event-name': 'testing' })
    fetch('http://localhost:3000/emit', { method: 'put', body: eventBody, headers: { 'Content-Type': 'application/json' } }).then(response => response.text()).then(body => this.eventsResults.push(body))
  }
}
</script>

<style scoped>

</style>
