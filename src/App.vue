/* eslint-disable */
<template>
  <div id="app">
    <PostForm />
    <h1>Number os posts: {{ postsCount }}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
import PostForm from "./components/PostForm";
export default {
  name: "app",
  computed: mapGetters(["validPosts", "postsCount"]),
  methods: mapActions(["fetchPosts"]),
  components: { PostForm },
  async mounted() {
    //this.$store.dispatch("fetchPosts");
    this.fetchPosts(10);
  }
};
</script>
<style>
#app {
  margin: 60px auto;
  padding: 30px;
  max-width: 400px;
}

.post {
  background-color: aqua;
  margin-bottom: 20px;
  border: 1px solid purple;
  padding: 10px;
}
</style>
