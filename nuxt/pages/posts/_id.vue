<template>
  <div>
    <h1>{{ post.title }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: {}
    }
  },
  async fetch() {
    this.post = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`).then(res =>
      res.json()
    )
  }
}
</script>
