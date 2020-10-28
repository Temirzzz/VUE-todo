<template>
    <div>
        <ul>
            <!-- {{ todos }} -->
            <TodoItem 
            v-for='(todo, i) in todos' :key="todo.id"
            v-bind:todo='todo' 
            v-bind:index="i"
            v-on:remove-todo="removeTodo"
            />
        </ul>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
    props: ['todos'],
    components: {
        TodoItem  
    },
    methods: {
        removeTodo(id) {
            //console.log(id);
            this.$emit('remove-todo', id)
        }
    }
}



</script>

<style scoped>
    ul {
        width: 500px;
        list-style: none;
        margin: 50px auto;
        padding: 0;
    }
</style>