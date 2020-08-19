<template>
  <div class="combat-counter">
    <h1>Combat Counter</h1>
  <div>
    <label>Count: {{ count }}</label>
    <button v-on:click="incrementCount">+</button>
    <button v-on:click="decrementCount">-</button>
  </div>
    <ul>
      <li v-for="character in characters"
        v-bind:key="character.name"> <!-- TODO generate unique key -->
        <character :character="character" />
      </li>
    </ul>
    <button>Add Combatant</button>
  </div>
</template>

<script>
import Character from './Character.vue'

export default {
  name: 'CombatCounter',
  components: {
    Character
  },
  methods: {
    incrementCount: function () {
      this.count = (this.count * 1) + 1 // coerce count as a number rather than string concatenation
      for (let character of this.characters) {
        character.secondsLeft -= 1
      }
    },
    decrementCount: function () {
      this.count -= 1
      for (let character of this.characters) {
        character.secondsLeft = (character.secondsLeft * 1) + 1
      }
    }
  },
  data: function() {
    return {
      count: 0,
      characters: [{name: "adventure", action: "attack", secondsLeft: 5}]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0.5rem;
  border: solid 1px;
}
li {
  display: inline;
  border: solid 1px;
  padding: 0.5rem;
}
a {
  color: #42b983;
}
</style>
