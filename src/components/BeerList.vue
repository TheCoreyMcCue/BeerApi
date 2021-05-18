<template>
  <div class="BeerList">
    <h1>List of Beers</h1>
    <div>
      <table border="1px">
        <tr>
          <td>Name</td>
          <td>ABV</td>
          <td>Date</td>
        </tr>
        <tr v-for="index in 10" :key="index">
          <td>{{ beers[index].name }}</td>
          <td>{{ beers[index].abv }}</td>
          <td>{{ beers[index].first_brewed }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
export default {
  name: "BeerList",
  data() {
    return { beers: undefined };
  },
  mounted() {
    Vue.axios.get("https://api.punkapi.com/v2/beers").then((response) => {
      this.beers = response.data;
      console.log(response.data);
    });
  },
};
</script>
