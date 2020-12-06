<template>
  <div>
    <div v-for="post in posts" :key="post.id">
      <nuxt-link v-bind:to="'/posts/' + post.id">
        <h1>{{ post.title }}</h1>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: []
    }
  },
  async fetch() {
    this.posts = await fetch('https://api.nuxtjs.dev/posts').then(res =>
      res.json()
    )
  }
}
</script>
