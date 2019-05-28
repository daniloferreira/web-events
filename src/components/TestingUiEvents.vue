<template>

  <div>
    <button v-on:click="testingGet">
      Emit event
    </button>

    <select name="hardChoices" @change="onSelectChanged($event)" class="form-control"  v-model="selectedItem">
      <option value="1">User selected 1</option>
      <option value="2">User selected 2</option>
    </select>
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
  selectedItem: String = '';

  onSelectChanged(event) {
    const eventBody = JSON.stringify({ 'event-type': 'select', 'event-name': event.target.name, 'custom-data': { 'item-selected': this.selectedItem } })
    fetch('http://localhost:3000/emit', { method: 'put', body: eventBody, headers: { 'Content-Type': 'application/json' } }).then(response => response.text()).then(body => this.eventsResults.push(body))
  }

  testingGet = (event) => {
    const eventBody = JSON.stringify({ 'event-type': 'click', 'event-name': 'testing', 'custom-data': { 'item-selected': event.target.id } })
    fetch('http://localhost:3000/emit', { method: 'put', body: eventBody, headers: { 'Content-Type': 'application/json' } }).then(response => response.text()).then(body => this.eventsResults.push(body))
  }
}
</script>

<style scoped>

</style>
