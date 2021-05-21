<template>
  <div class="SortedAbv">
    <h1>Our top 10 Beers (sorted by ABV)</h1>
    <div class="container">
      <div v-for="item in beersSorted" :key="item" class="card-group d-flex">
        <div class="card mb-2 py-2">
          <a v-bind:href="'#/beer/' + item.id">
            <img
              :src="item.image_url"
              id="beer-img"
              class="card-img-top"
              alt="..."
            />
          </a>
          <div class="card-body">
            <h5 class="card-title">{{ item.name }}</h5>
            <p class="card-text">
              <small class="text-muted">ABV {{ item.abv }}%</small>
            </p>
            <p class="card-text">{{ item.description }}</p>
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
    return { beers: undefined, beersSorted: undefined };
  },
  mounted() {
    Vue.axios.get("https://api.punkapi.com/v2/beers").then((response) => {
      this.beers = response.data;
      this.beersSorted = response.data.slice(0, 10).sort((a, b) => {
        return a.abv - b.abv;
      });
      console.log(this.beersSorted);
      this.url = "/beer/";
    });
  },
};
</script>

<style scoped>
.SortedAbv {
  background-image: url("https://images.unsplash.com/photo-1505075106905-fb052892c116?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2850&q=80");
}

h1 {
  color: white;
  border-bottom: 1px solid white;
}

.card {
  max-height: 50%;
}

#beer-img {
  max-height: 38vh;
  width: auto;
  object-fit: contain;
}
</style>
