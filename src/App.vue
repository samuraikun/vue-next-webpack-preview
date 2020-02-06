<template lang="pug">
.app
  img.app__logo(src="./logo.png")
  h1.app__title Hello Vue 3!
  button.app__button(@click="inc") Clicked {{ count }} times.
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const count = ref(0)
    const inc = () => {
      count.value++
    }

    return {
      count,
      inc
    }
  }
}
</script>

<style lang="scss" scoped>
.app {
  display: grid;
  grid-template:
    " . logo  . " auto
    " . title . " auto
    " .   .   . " 50px
    " . button . " auto
    " .   .    . " 1fr/
    1fr auto 1fr;

  &__logo {
    grid-area: logo;
    width: 200px;
  }

  &__title {
    grid-area: title;
    font-family: Arial, Helvetica, sans-serif;
    color: green;
  }

  &__button {
    grid-area: button;
    border-radius: 30px;
  }
}
</style>
