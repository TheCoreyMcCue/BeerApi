<template>
  <div class="beer">
    <h1>Random beer</h1>
    <div class="container d-flex justify-content-center">
      <div class="card" style="width: 15rem" v-if="beer">
        <img
          v-if="beer.image_url"
          :src="beer.image_url"
          alt=""
          id="beer-img"
          class="card-img-top"
        />
        <div class="card-body">
          <h5 class="card-title">{{ beer.name }}</h5>
          <p class="text-muted">ABV: {{ beer.abv }}%</p>
          <p class="card-text">
            {{ beer.description.substring(0, 170) + ".." }}
          </p>
        </div>
      </div>
    </div>
    <button @click="showBeer" class="btn btn-primary mt-2">
      Beer Randomizer
    </button>
  </div>
</template>

<script lang="ts">
import vue from "vue-property-decorator";
import axios from "axios";

export default {
  name: "Test",
  props: {},
  data() {
    return {
      beer: "",
      beer2: "",
    };
  },
  methods: {
    async showBeer() {
      let config = {
        headers: {
          Accept: "application/json",
        },
      };
      const beer = await axios.get(
        "https://api.punkapi.com/v2/beers/random",
        config
      );
      this.beer = beer.data[0];
    },
    async showBeer2() {
      let config = {
        headers: {
          Accept: "application/json",
        },
      };
      const beer = await axios.get(
        "https://api.punkapi.com/v2/beers/1",
        config
      );
      return (this.beer2 = beer.data[0]);
    },
  },
};
</script>

<style scoped>
#beer-img {
  max-height: 38vh;
  width: auto;
  object-fit: contain;
}
.card {
  max-height: 80vh;
}
.card-text {
  /* display:inline-block; */
  /* white-space: nowrap; */
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100ch;
}
</style>
