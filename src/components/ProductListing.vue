<template>
  <div>
    <!-- <h1>All data {{ pData.length }}</h1>
    <h2>{{ pData }}</h2> -->
    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <h2>{{ post.author }}</h2>
    </div>
    <!-- <h2>{{ posts }}</h2> -->
  </div>
</template>

<script>
//import ProductData from "../data/data.json";
import axios from "axios";
export default {
  name: "ProductListing",
  data() {
    return {
      posts: []
    };
  },
  // computed: {
  //   title() {
  //     return {
  //       postTitle: this.posts.title
  //     };
  //   }
  // },
  created() {
    axios
      .get("http://localhost:3000/posts")
      .then(response => {
        //console.log(response.data);
        this.posts = response.data;
      })
      .catch(error => {
        console.log("There was an error:" + error.response);
      });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
