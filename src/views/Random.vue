<template>
  <div class="Beer pb-3">
    <a href="/" id="arrow"><i class="fas fa-arrow-left"></i> </a>
    <h1>Learn about a random beer</h1>
    <div class="container d-flex justify-content-center">
      <div class="card" v-if="beer">
        <img
          v-if="beer.image_url"
          :src="beer.image_url"
          alt="picture of selected beer"
          id="beer-img"
          class="card-img-top pt-2"
        />
        <img
          v-else
          id="beer-img"
          src="../assets/logo.png"
          class="card-img-top pt-2 px-2 alt-img"
          alt=""
        />
        <div class="card-body">
          <h5 class="card-title">{{ beer.name }}</h5>
          <p class="text-muted">ABV: {{ beer.abv }}%</p>
          <p class="card-text">
            {{ beer.description.substring(0, 120) + ".." }}
          </p>
        </div>
      </div>
    </div>
    <button @click="showBeer" class="btn btn-info mt-3">Beer Randomizer</button>
  </div>
</template>

<script lang="ts">
import axios from "axios";

export default {
  name: "Random",
  props: {},
  data() {
    return {
      beer: null,
    };
  },
  methods: {
    async showBeer() {
      let config = {
        headers: {
          Accept: "application/json",
        },
      };
      let beer = await axios.get(
        "https://api.punkapi.com/v2/beers/random",
        config
      );
      this.beer = beer.data[0];
    },
  },
};
</script>

<style scoped>
.Beer {
  min-height: 100vh;
  background-image: url("https://images.unsplash.com/photo-1505075106905-fb052892c116?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2850&q=80");
}

h1 {
  color: white;
}

#beer-img {
  max-height: 38vh;
  width: auto;
  object-fit: contain;
}

.card {
  max-height: 80vh;
  background-color: #dda15e;
  min-width: 50%;
  margin-top: 5%;
}
.card-text {
  /* display:inline-block; */
  /* white-space: nowrap; */
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 100vh;
}

#arrow {
  color: white;
  font-size: 1.5rem;
  padding-top: 8%;
  position: absolute;
  left: 10%;
}
#arrow:hover {
  color: #dda15e;
}
</style>
