<template>
  <div id="app" class="container">
    <h1 class="text-center">투두 투두 투두</h1>
      <CompletedTodo :todos="todos"/>
      <AddTodo @add-todo="addTodo"/>
    <hr>
      
      <TodoList 
        :todos="todos"
        @toggle-checkbox="toggleCheckbox"
        @delete-todo="deleteTodo"
      />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import AddTodo from './components/AddTodo.vue';
import CompletedTodo from './components/CompletedTodo.vue';
export default {
    components: { TodoList, AddTodo, CompletedTodo },
    data() {
      return {
        todos: [
          { id: 1, text: '뷰 공부하기', checked: false},
          { id: 2, text: '집에서 놀기', checked: false}
        ],
      }
    },
    methods: {
      addTodo(e) {
        this.todos.push({ 
          id: this.todos.length+1, 
          text: e, 
          checked: false 
        })
      },
      toggleCheckbox({id, checked}) {
        const index = this.todos.findIndex(todo => {
          return todo.id === id
        })
        this.todos[index].checked = checked
      },
      deleteTodo({id}) {
        // const index = this.todos.findIndex(todo => {
        //   return todo.id === id
        // })
        // this.todos.splice(index,1)
        this.todos = this.todos.filter(todo =>  todo.id !== id)
      }
    }
}
</script>