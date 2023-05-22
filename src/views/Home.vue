<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>
      <p>loading...</p>
    </div>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue'
// component imports
import PostList from '../components/PostList.vue'
import fetchPosts from '../composables/fetchPosts'

export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const { posts, error, load } = fetchPosts()
    load()
    return { posts, error }
  },
}
</script>
