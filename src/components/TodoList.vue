<template>
    <div>
        <TodoItem 
            v-for="todo in todos"  
            :key="todo.id"
            :todo="todo"
            @toggle-checkbox="toggleCheckbox"
            @delete-todo="deleteTodo"
        />
    </div>
</template>
<script>
import TodoItem from './TodoItem.vue';
export default {
    components: { TodoItem },
    props: {
        todos: {
            type: Array,
            required: true
        }
    },
    methods: {
        toggleCheckbox(value) {
            this.$emit('toggle-checkbox', value)
        },
        deleteTodo(todoId) {
            this.$emit('delete-todo', todoId)
        },
    }
}
</script>

<style scoped>

</style>
