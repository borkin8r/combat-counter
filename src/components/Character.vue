<template>
    <div class="character">
        <label>Name: 
            <input v-bind:value="character.name"
            v-on:input="updateName($event.target.value)" type="text"/>
        </label>
        <label>Action: 
            <input v-bind:value="character.action"
            v-on:input="updateAction($event.target.value)" type="text"/>
        </label>
        <label>Seconds Until Action: 
            <input v-bind:value="character.secondsLeft"
            v-on:input="updateSecondsLeft($event.target.value)" type="number"/>
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
        updateSecondsLeft: function (updatedSecondsLeft) {
            this.$emit('update-seconds-left', updatedSecondsLeft)
        },
        updateName: function (updatedName) {
            this.$emit('update-name', updatedName)
        },
        updateAction: function (updatedAction) {
            this.$emit('update-action', updatedAction)
        }
    }
}
</script>

<style scoped>
    .character {
        display: inline;
    }
    label {
        margin-left: 5px;
    }
</style>