<template>
  <div class="AB beer-show">
    <img :src="beer.image_url" alt="" />
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
export default {
  name: "AB",
  data() {
    return { beer: undefined };
  },
  mounted() {
    Vue.axios.get("https://api.punkapi.com/v2/beers/7").then((response) => {
      this.beer = response.data[0];
      console.log(this.beer);
      this.url = "/beer/";
    });
  },
};
</script>

<style>
.beer-show {
  min-height: 100vh;
  background-size: cover;
  background-position: center;
  background-image: url("https://images.unsplash.com/photo-1581338772961-e1a4c9b36580?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2734&q=80");
}
</style>
