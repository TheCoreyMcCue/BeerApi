<template>
  <div class="BeerList pb-4">
    <h1 class="pt-3">Our top 10 Beers</h1>
    <div class="container">
      <div v-for="index in 10" :key="index" class="card-group">
        <div class="card mb-2 py-2 d-flex">
          <a v-bind:href="'#/beer/' + beers[index].id">
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
.BeerList {
  background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("https://images.unsplash.com/photo-1505075106905-fb052892c116?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2850&q=80");
}

h1 {
  color: white;
  border-bottom: 1px solid white;
}

.card {
  /* max-height: 10%; */
  background-color: #dda15e;
  /* max-width: 40%; */
}

.card-title {
  font-weight: bold;
}

#beer-img {
  max-height: 38vh;
  width: auto;
  object-fit: contain;
}
</style>
