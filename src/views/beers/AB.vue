<template>
  <div class="AB beer-show">
    <div class="container">
      <h1>{{ beer.name }}</h1>
      <h3>{{ beer.tagline }}</h3>
      <p>{{ beer.description }}</p>
      <h5 class="percentage pb-3">
        <strong> Alcohol Percentage: {{ beer.abv }}%</strong>
      </h5>
      <img :src="beer.image_url" id="beer-img" alt="" />
      <h5 class="pt-4">Pairs well with: {{ beer.food_pairing[0] }}<br /></h5>
    </div>
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
h1,
h3,
h5,
p {
  color: white;
}
.percentage {
  /* text-align: left; */
}

.card {
  position: absolute;
  top: 50%;
  left: 50%;
  margin-top: -50px;
  margin-left: -135px;
  width: 100px;
  height: 100px;
}
#beer-img {
  max-height: 38vh;
  width: auto;
  object-fit: contain;
}

.beer-show {
  min-height: 100vh;
  background-size: cover;
  background-position: center;
  background-color: #344d5b;
  /* background-image: url("https://images.unsplash.com/photo-1600366060302-9fb7682b062b?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=668&q=80"); */
}
</style>
