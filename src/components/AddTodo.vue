<template>
    <input 
      type="text" 
      class="w-100 p-2" 
      placeholder="할일을 입력하세요"
      @keyup.enter="addTodo"
      v-model="inputValue"
    >
</template>

<script>
export default {
    data() {
      return {
        inputValue: ""
      }
    },
    methods: {
        addTodo(e) {
            this.$emit('add-todo', e.target.value)
            this.inputValue = ""
        }
    }
}
</script>

<style scoped>

</style>