<template>
  <div class="posts-new">
    <form v-on:submit.prevent="submit()">
      <h1>Create a new post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <div class="form-group">
        <label>User ID:</label> 
        <input type="integer" class="form-control" v-model="user_id">
      </div>
      <div class="form-group">
        <label>Title:</label>
        <input type="string" class="form-control" v-model="title">
      </div>
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="body">
      </div>
      <div class="form-group">
        <label>Image:</label>
        <input type="text" class="form-control" v-model="image">
      </div>
      <input type="submit" class="btn btn-primary" value="Submit">
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      user_id: "",
      title: "",
      body: "",
      image: "",
      errors: [],
    };
  },
  methods: {
    submit: function () {
      var params = {
        user_id: this.userID,
        title: this.title,
        body: this.body,
        image: this.image,
      };
      axios
        .post("/api/posts", params)
        .then((response) => {
          this.$router.push("/posts");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>