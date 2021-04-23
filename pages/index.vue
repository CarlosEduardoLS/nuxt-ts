<template>
  <div>
    <h1>Postagem</h1>
    <p>{{ titlePost }}</p>
    <p>{{ content }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

const sleep = () => {
  return new Promise((resolve) => setTimeout(resolve, 1500))
}

export default Vue.extend({
  layout: 'dashboard',
  async asyncData() {
    await sleep()
    const titlePost = 'My Post Title'
    const content = 'Lorem ipsum dolor sit...'
    return { titlePost, content }
  },
  data() {
    return {
      title: 'Título Dinâmico',
      titlePost: '',
      content: '',
    }
  },
  head(this: any) {
    return {
      title: this.title,
    }
  },
  mounted() {
    this.$axios.$get('/posts')
  },
})
</script>

<style scoped>
a.nuxt-link-exact-active {
  font-weight: bold;
}
</style>
