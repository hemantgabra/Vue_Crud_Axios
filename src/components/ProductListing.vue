<template>
  <div>
    <ul>
      <li>{{ dummyData }}</li>
    </ul>
    <ul>
      <li><strong>ID</strong></li>
      <li><strong>Email ID</strong></li>
      <li><strong>First Name</strong></li>
      <li><strong>Last Name</strong></li>
      <li><strong>Image</strong></li>
    </ul>
    <ul v-for="printDummyData in dummyData" :key="printDummyData.id">
      <li>{{ printDummyData.page }}</li>
      <li>{{ printDummyData.email }}</li>
      <li>{{ printDummyData.first_name }}</li>
      <li>{{ printDummyData.last_name }}</li>
      <li><img :src="printDummyData.avatar" /></li>
    </ul>
  </div>
</template>

<script>
//import ProductData from "../data/data.json";
import axios from "axios";
export default {
  name: "ProductListing",
  data() {
    return {
      dummyData: null
    };
  },
  created() {
    axios.get("https://reqres.in/api/users?page=1").then(response => {
      this.dummyData = response.data;
      //console.log(response.data);
    });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style: none;
  display: flex;
  flex-wrap: nowrap;
}
li {
  border: 1px solid #e1e1e1;
  width: 100%;
  padding: 20px;
}
</style>
