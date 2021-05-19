<template>
  <div class="BeerList">
    <h1>List of Beers</h1>
    <div class="container">
      <div v-for="index in 10" :key="index" class="card-group d-flex">
        <div class="card mb-2 py-2">
          <a v-bind:href="'#/beers/' + beers[index].id">
            <img
              :src="beers[index].image_url"
              id="beer-img"
              class="card-img-top"
              alt="..."
            />
          </a>
          <div class="card-body">
            <h5 class="card-title">{{ beers[index].name }}</h5>
            <p class="card-text">
              <small class="text-muted">ABV {{ beers[index].abv }}%</small>
            </p>
            <p class="card-text">{{ beers[index].description }}</p>
          </div>
        </div>
      </div>
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
      this.url = "/beer/";
    });
  },
};
</script>

<style scoped>
#beer-img {
  max-height: 38vh;
  width: auto;
  object-fit: contain;
}
</style>
