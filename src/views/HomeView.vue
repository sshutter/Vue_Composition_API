<template>
  <div class="class">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" v-if="showPosts" />
    </div>
    <div v-else>Loading...</div>
    <button @click="showPosts = !showPosts">Toggle Posts</button>
    <button @click="posts.pop()">Delete a post</button>
  </div>
</template>

<script>
import PostList from "../components/PostList.vue";
import getPosts from "../composables/getPosts";
import { ref } from "vue";

export default {
  name: "Home",
  components: { PostList },
  setup() {
    const showPosts = ref(true);

    const { posts, error, load } = getPosts();

    load();

    return { posts, showPosts, error };
  },
};
</script>

<style>
button {
  padding: 10px;
  background: #2d3981;
  color: white;
  border: none;
  border-radius: 10px;
  letter-spacing: 1px;
  font-size: 0.8em;
  margin: 10px;
}

button:hover {
  cursor: pointer;
  background: #161c40;
}
</style>
