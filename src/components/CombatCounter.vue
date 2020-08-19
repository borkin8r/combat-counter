<template>
  <div class="combat-counter">
    <h1>Combat Counter</h1>
  <div>
    <label>Count: {{ count }}</label>
    <button v-on:click="incrementCount">+</button>
    <button v-on:click="decrementCount">-</button>
  </div>
    <ul>
      <li v-for="(character, index) in characters"
        v-bind:key="character.id"> <!-- TODO generate unique key -->
        <character :character="character" 
                  v-on:update-seconds-left="character.secondsLeft = $event"
                  v-on:update-name="character.name = $event"
                  v-on:update-action="character.action = $event"
        ></character>
        <button v-on:click="removeCharacter(index)">X</button>
      </li>
    </ul>
    <button v-on:click="addCharacter()">Add Combatant</button>
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
      this.count++ // coerce count as a number rather than string concatenation
      for (let character of this.characters) {
        character.secondsLeft--
      }
    },
    decrementCount: function () {
      this.count--
      for (let character of this.characters) {
        character.secondsLeft++
      }
    },
    removeCharacter: function (anIndex) {
      this.characters.splice(anIndex, 1)
    },
    addCharacter: function () {
      this.characters.push({id: this.nextId++, name: "", action: "", secondsLeft: 0})
    }
  },
  data: function() {
    return {
      count: 0,
      nextId: 1,
      characters: [{id: 0, name: "adventure", action: "attack", secondsLeft: 5}]
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
  display: block;
  list-style-type: none;
  padding: 0.5rem;
  border: solid 1px;
}
li {
  border: solid 1px;
  padding: 0.5rem;
  margin-bottom: 5px;
}
a {
  color: #42b983;
}
</style>
