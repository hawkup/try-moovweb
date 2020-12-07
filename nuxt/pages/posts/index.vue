<template>
  <div>
    <div v-for="post in posts" :key="post.id">
      <Prefetch v-bind:url="'https://api.nuxtjs.dev/posts/' + post.id">
        <nuxt-link v-bind:to="'/posts/' + post.id">
          <h1>{{ post.title }}</h1>
        </nuxt-link>
      </Prefetch>
    </div>
  </div>
</template>

<script>
import { Prefetch } from '@xdn/vue'

export default {
  components: {
    Prefetch
  },
  data() {
    return {
      posts: []
    }
  },
  async fetch() {
    this.posts = await fetch('https://jsonplaceholder.typicode.com/posts').then(res =>
      res.json()
    )
  }
}
</script>
