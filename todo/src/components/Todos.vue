<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" @isCompletedChanged="todo.completed = $isCompletedChanged" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"],
    methods: {
        isCompletedChanged() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>

</style>