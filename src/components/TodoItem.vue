<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input type="checkbox" v-on:change="todo.completed = !todo.completed">
            <strong>{{ index + 1 }}</strong>
            {{ todo.title | uppercase }}
        </span>
        <button class="btn_close" 
        v-on:click="$emit('remove-todo', todo.id)"
        >&times;</button>
    </li>
</template>

<script>

export default {
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
        uppercase(value) {
            return value.toUpperCase();
        }
    }
}

</script>

<style scoped>
    li {
        display: flex;
        justify-content: space-between;
        border: 1px solid #ccc;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
        margin-left: 2rem;
        align-items: center;
    }
    input {
        margin-right: 1rem;
    }
    .btn_close {
        width: 25px;
        height: 25px;
        background:#4682B4;
        border: none;
        border-radius: 3px;
        color: #FFF;
        cursor: pointer;
    }
    .done {
        text-decoration: line-through;
    }
</style>