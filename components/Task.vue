<template>
    <div :class="`task ${task.done ? 'is-complete' : ''}`">
        <div class="content">{{ task.content }}</div>
        <button @click="toggleDone">{{ task.done ? 'Undo' : 'Complete' }}</button>
        <button @click="removeTask" class="delete">Delete</button>
    </div>
</template>

<script>
export default {
    props: ['task'],
    methods: {
        toggleDone() {
            this.$store.commit('TOGGLE_TASK', this.task)
        },
        removeTask(task) {
            this.$store.commit('REMOVE_TASK', this.task)
        }
    }
}
</script>

<style>

</style>