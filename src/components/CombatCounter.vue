<template>
  <div class="combat-counter">
    <div class="counter">
      <h1>Count: {{ count }}</h1>
      <button v-on:click="incrementCount">Advance Time 1 Second</button>
      <button v-on:click="decrementCount">Rewind Time 1 Second</button>
    </div>
    <div class="controls">
      <button class="success" v-on:click="addCharacter()">Add Combatant</button>
    </div>
    <table class="primary">
      <thead>
        <th>Name</th>
        <th>Action</th>
        <th>Seconds Left</th>
        <th></th>
      </thead>
      <tbody>
        <tr v-for="(character, index) in characters"
            v-bind:class="{ ready: character.secondsLeft <= 0 }"
            v-bind:key="character.id">
          <td>
            <input v-model="character.name"
            v-on:input="updateName($event.target.value)" type="text"/>
          </td>
          <td> 
              <input v-model="character.action"
              v-on:input="updateAction($event.target.value)" type="text"/>
          </td>
          <td>
              <input v-model="character.secondsLeft"
              v-on:input="updateSecondsLeft($event.target.value)" type="number"/>
          </td>
          <button class="error" v-on:click="removeCharacter(index)">X</button>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'CombatCounter',
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
a {
  color: #42b983;
}
.ready {
    background-color: red;
}
table {
  display: initial;
}
th {
  text-align: center;
}
tr, thead {
  border: 1px solid black;
}
.counter > label, .counter > button {
  margin-left: 5px;
}
.counter > label {
  font-weight: bold;
  font-size: large;
}

</style>
