<template lang="pug">
.app
  .app__header
    h1.app__header__title Vue3 Todo
  .app__main
    input.app__main__new-todo(
      autofocus=""
      autocomplete="off"
      placeholder="TODOを追加"
      value=""
      @keyup.enter="addTodo"
    )
    Suspense
      template(#default)
        TodoList
      template(#fallback)
        | Loading...
</template>

<script>
import { ref, reactive, onMounted } from "vue"
import TodoList from "./TodoList.vue"

export default {
  components: {TodoList},
  setup() {
    const newTodo = ref("")
    const fetchTodos = () => {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          return resolve(data)
        }, 2000)
      })
    }

    const onChange = (e) => {
      const completedTodoIndex = e.target.value;
      state.todos.filter
    }

    const addTodo = (e) => {
      const todo = Object.assign("", e.target.value)
      state.todos.push({ content: todo, completed: false })
    }

    return {
      newTodo,
      state,
      addTodo,
      onChange
    }
  }
}
</script>

<style lang="scss" scoped>
.app {
  display: grid;
  grid-template:
    " header header header " 70px
    "   .      .      .    " 30px
    "   .    main     .    " auto
    "   .      .      .    " 1fr/
    1fr   auto    1fr;

  &__header {
    grid-area: header;
    width: 100%;
    border-bottom: 1px solid black;

    &__title {
      text-align: center;
      font-family: Arial, Helvetica, sans-serif;
      color: green;
    }
  }

  &__main {
    grid-area: main;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    &__new-todo {
      box-sizing: border-box;
      border-radius: 5px;
      min-height: 40px;
      padding: 0 10px;
      font-size: 14px;
      letter-spacing: .4px;
      outline: none;
      transition: .3s;
    }

    &__todo-list {
      list-style: none;
    }
  }
}
</style>
