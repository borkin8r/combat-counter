<template>
  <div class="combat-counter">
    <h1>Combat Counter</h1>
  <div>
    <label>Count: {{ count }}</label>
    <button>+</button>
    <button>-</button>
  </div>
    <ul>
      <li>
        <label>Name: 
          <input type="text">
        </label>
        <label>Action: 
          <input type="text">
        </label>
        <label>Seconds Until Action: 
          <input type="text">
        </label>
        <button>X</button>
      </li>
    </ul>
    <button>Add Combatant</button>
  </div>
</template>

<script>
export default {
  name: 'Combat Counter',
  props: {
    count: Number
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
