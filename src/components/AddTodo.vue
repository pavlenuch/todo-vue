<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
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

                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }
}
</script>


<style scoped>
    form {
        display: flex;
        width: 410px;
        margin: 15px auto 15px auto;
    }
    input {
        width: 300px;
        height: 20px;
        margin-right: 10px;
    }
    button {
        background-color: skyblue;
        border: 1px slategray solid;
        border-radius: 3px;
        outline: none;
        cursor: pointer;
        width: 90px;
    }
</style>>
