<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>
    <h1> title: {{post.title}}</h1>
    <h1> post: {{post.body}}</h1>
    <h1> image: {{post.image}}</h1>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      post: {},
    };
  },
  created: function () {
    this.postsShow();
  },
  methods: {
    postsShow: function () {
      console.log("in posts show");
      axios.get("/api/posts/2").then((response) => {
        console.log(response.data);
        this.post = response.data;
      });
    },
  },
};
</script>
