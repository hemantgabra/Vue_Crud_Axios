<template>
  <div>
    <nav
      class="pagination is-small is-centered mr-5 ml-5"
      role="navigation"
      aria-label="pagination"
    >
      <a class="pagination-previous">Previous</a>
      <a class="pagination-next" @click="nextPageListing()">Next page</a>
      <ul class="pagination-list">
        <li>
          <a class=" is-current pagination-link" aria-label="Goto page 1">1</a>
        </li>
        <!-- <li><span class="pagination-ellipsis">&hellip;</span></li> -->
        <li><a class="pagination-link" aria-label="Goto page 45">2</a></li>
        <li><a class="pagination-link" aria-label="Goto page 86">3</a></li>
        <li><a class="pagination-link" aria-label="Goto page 86">4</a></li>
        <li><a class="pagination-link" aria-label="Goto page 86">5</a></li>
        <!-- <li>
          <a class="pagination-link" aria-label="Page 46" aria-current="page"
            >46</a
          >
        </li>
        <li><a class="pagination-link" aria-label="Goto page 47">47</a></li>
        <li><span class="pagination-ellipsis">&hellip;</span></li> -->
      </ul>
    </nav>
    <h1 class="subtitle">
      {{ firstIndexOfData }} - {{ firstLoadListingData.length }} From
      {{ listingData.length }}
    </h1>
    <ul class="listing-data">
      <li><strong>ID</strong></li>
      <li><strong>Title</strong></li>
      <li><strong>Image</strong></li>
    </ul>
    <ul
      class="listing-data"
      v-for="printListingData in firstLoadListingData"
      :key="printListingData.id"
    >
      <li>{{ printListingData.id }}</li>
      <li>{{ printListingData.title }}</li>
      <li><img :src="printListingData.thumbnailUrl" /></li>
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
      //rowData: null,
      listingData: [],
      firstIndexOfData: 1
    };
  },
  computed: {
    firstLoadListingData() {
      return this.listingData.slice(0, 100);
    }
  },
  methods: {
    nextPageListing() {
      //alert(this.firstLoadListingData.length);
      this.firstLoadListingData += 100;
    }
  },
  created() {
    axios.get("https://jsonplaceholder.typicode.com/photos").then(response => {
      //this.rowData = response.data;
      this.listingData = response.data;
      console.log(this.listingData);
    });
    // .catch(err => {
    //   this.error = err.data;
    // });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul.listing-data {
  list-style: none;
  display: flex;
  flex-wrap: nowrap;
}
ul.listing-data li {
  border: 1px solid #e1e1e1;
  width: 100%;
  padding: 20px;
}
</style>
