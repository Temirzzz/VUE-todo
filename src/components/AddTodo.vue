<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button class="btn_add" type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo);
                this.title = '';
            }
        }
    }
}
</script>

<style scoped>
    form {
        width: 500px;
        margin: 20px auto;
        display: flex;
        flex-direction: column;
    }
    input {
        width: 500px;
        height: 40px;
    }
    .btn_add {
        width: 110px;
        height: 35px;
        background: #2F4F4F;
        border: none;
        cursor: pointer;
        margin: 20px auto;
        color: #fff;
    }
</style>

