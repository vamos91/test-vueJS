<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <todoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"></todoItem>
        </div>
    </div>
</template>

<script>
import todoItem from './TodoItems'
export default {
    name: "Todos",
    props: ["todos"],
    components: {
        todoItem
    }
}
</script>

<style scoped>

</style>