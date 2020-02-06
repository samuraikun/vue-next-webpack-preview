<template lang="pug">
.app
  .app__header
    h1.app__header__title Vue3 Todo
  .app__main
    input.app__main__new-todo(
      autofocus=""
      autocomplete="off"
      placeholder="TODOを追加"
      v-model="newTodo"
      @keyup.enter="addTodo"
    )
    ul.app__main__todo-list(v-for="(todo, i) in todos" :key="i")
      li.app__main__todo
        input.todo__checkbox(type="checkbox" :value="i" :checked="todo.completed" @change="onChange")
        span.todo__content {{ todo.content }}
</template>

<script>
import { ref, reactive } from "vue"

export default {
  setup() {
    const data = [
      { content: "Vue3を完全理解する", completed: false },
      { content: "Ember.jsを殺す", completed: false },
      { content: "IEを殺す", completed: false }
    ]
    const newTodo = ref("")
    const todos = reactive(data)

    const onChange = (e) => {
      const completedTodoIndex = e.target.value;
      todos.filter
    }

    const addTodo = (e) => {
      const todo = Object.assign("", newTodo)
      todos.push({ content: todo, completed: false })
    }

    return {
      newTodo,
      todos,
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
