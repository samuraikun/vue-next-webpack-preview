<template lang="pug">
ul.app__main__todo-list(v-for="(todo, i) in todos" :key="i")
  li.app__main__todo
    input.todo__checkbox(type="checkbox" :value="i" :checked="todo.completed" @change="onChange")
    span.todo__content {{ todo.content }}
</template>

<script>
export default {
  async setup() {
    const data = [
      { content: "Vue3を完全理解する", completed: false },
      { content: "GraphQLを完全理解する", completed: false },
      { content: "CSSを完全理解する", completed: false }
    ]
    const fetchTodos = () => {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          return resolve(data)
        }, 2000)
      })
    }

    const todos = await fetchTodos()

    return {
      todos
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
