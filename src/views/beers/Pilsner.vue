<template>
  <div>
    <h1>{{ beer[0].name }}</h1>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, axios);
export default {
  name: "Pilsner",
  data() {
    return { beer: undefined };
  },
  mounted() {
    Vue.axios.get("https://api.punkapi.com/v2/beers/4").then((response) => {
      this.beer = response.data;
      this.url = "/beer/";
    });
  },
};
</script>
