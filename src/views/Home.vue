<template>
  <div class="home">
    <div>
      <h1 class="fw-bolder">TODO</h1>
    </div>

    <form @submit.prevent="addTodo(todo)">
      <div class="input-group mt-4">
        <input class="form-control" v-model="todo.description" type="text" name="todoContent" id="todoContent">
        <button class="btn btn-primary">Adicionar</button>
      </div>
    </form>

    <section class="mt-5">
      <Todo v-for="t in todos" :key="t.id" @toggle="toggleTodo" @remove="removeTodo" :todo="t"/>
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Todo from '@/components/Todo.vue'

export default {
  name: 'Home',
  components: { Todo },
  data() {
    return { todos: [], todo: {checked: false} }
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now()
      this.todos.push(todo)
      this.todo = { checked: false }
    },

    toggleTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id)

      if(index > -1) {
        const checked = !this.todos[index].checked
        this.todos[index] = { ...this.todos[index], checked }
      }
    },

    removeTodo(todo) {
      const index = this.todos.findIndex(item => item.id === todo.id)

      if(index > -1) {
        // this.todos.splice(index, 1)
        delete(this.todos, index)
      }
    }
  }
}
</script>

<style scoped>
  .container {
    max-width: 600px !important;
  }
</style>