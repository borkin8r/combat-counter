<template>
    <div class="character">
        <label>Name: 
            <input v-bind:value="character.name" type="text"/>
        </label>
        <label>Action: 
            <input v-bind:value="character.action" type="text"/>
        </label>
        <label>Seconds Until Action: 
            <input v-bind:value="character.secondsLeft" type="number"/>
        </label>
    </div>
</template>

<script>
export default {
    name: 'character',
    props: {
        character: {
            name: String,
            action: String,
            secondsLeft: String
        }
    },
    methods: {
        
    }
}
</script>

<style scoped>
    .character {
        display: inline;
    }
</style>