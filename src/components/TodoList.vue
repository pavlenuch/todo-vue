<template>
    <div>
        <ul>
            <TodoItem 
                v-for="(todo, index) of todos"
                v-bind:todo="todo"
                v-bind:key="index"
                v-bind:index="index"
                @remove-todo="removeTodo"

            />
        </ul>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
export default {
    props:['todos'],
    components: {
        TodoItem
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id)
        }
    }
}
</script>

<style scoped src='./TodoList.module.css'></style>
