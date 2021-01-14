<template>
    <li>
        <span v-bind:class="{done: todo.completed}">
            <input 
                type="checkbox"
                 v-on:change="todo.completed = !todo.completed"
            >
            <strong>{{index+1}}</strong>
            {{todo.title | uppercase}}
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
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
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        width: 400px;
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin: 15px auto 15px auto;
        border-radius: 3px;
    }
    .rm {
        background-color: red;
        color: silver;
        border-radius: 50%;
        font-weight: bold;
        border: 0;
        outline: none;
        cursor: pointer;
    }
    input {
        margin-right: 10px;
    }
    .done {
        text-decoration: line-through;
    }
</style>