<template>
    <div v-bind:class="{ 'is-complete': todo.completed  }">
        <p>
            <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
            {{ todo.title }}
            <button class="del" v-on:click="$emit('del-todo', todo.id)">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItems",
    props: ["todo"],
    methods:{
        markComplete: function(){
            this.todo.completed = !this.todo.completed
        }
    }
}
</script>

<style scoped>
.is-complete{
    text-decoration: line-through;
}
</style>