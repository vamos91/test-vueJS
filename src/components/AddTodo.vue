<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Enter new task">
            <button type="submit">Add</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "addTodo",
    data(){
        return{
            title: ''
        }
    },
    methods:{
        addTodo: function(event) {
            event.preventDefault()
            const newTodo = {
                title: this.title,
                complete: false
            }
            this.$emit('add-todo', newTodo)
            this.title = ''
        }
    }
    
}
</script>

<style scoped>
form{
    display: flex;
}
</style>