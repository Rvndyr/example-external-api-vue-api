<template>
  <div class="home">
    <div v-for="post in posts" v-bind:key="post.id">{{ post.title }}</div>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      posts: [],
      articles: [],
    };
  },
  created: function () {
    this.indexPosts();
    this.indexNewsArticles();
  },
  methods: {
    indexPosts: function () {
      axios.get("https://jsonplaceholder.typicode.com/posts").then((response) => {
        console.log(response.data);
        this.posts = response.data;
      });
    },
    indexNewsArticles: function () {
      axios.get("http://localhost:3000/pages").then((response) => {
        console.log("NewsAPi:", response.data);
        this.articles = response.data;
      });
    },
  },
};
</script>
