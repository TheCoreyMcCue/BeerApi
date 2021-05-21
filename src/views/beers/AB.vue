<template>
  <div class="AB beer-show">
    <div class="container d-flex">
      <a href="/" id="arrow"><i class="fas fa-arrow-left"></i> </a>
      <div class="row justify-content-around">
        <!-- <img :src="beer.image_url" id="beer-img" alt="" /> -->
        <div class="col-6 content">
          <h1 class="beer-name">
            <i class="fas fa-beer icons"></i> {{ beer.name }}
          </h1>
          <h3>{{ beer.tagline }}</h3>
          <h6>First Brewed: {{ beer.first_brewed }}</h6>
          <p>{{ beer.description }}</p>
          <h5 class="pb-3">
            <strong class="percentage">
              <i class="fas fa-percent icons"></i> Alcohol Percentage:
            </strong>
            {{ beer.abv }}%
          </h5>
          <h5 class="pt-4">
            <i class="fas fa-utensils icons"></i>
            <strong class="percentage"> Pairs well with: </strong>
            {{ beer.food_pairing[0] }}<br />
          </h5>
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
h6,
p {
  color: white;
}

.percentage {
  font-weight: bold;
}

.beer-name {
  text-align: center;
  margin-bottom: 2rem;
}

h1,
h3 {
  font-weight: bold;
}

.content {
  min-width: 80vw;
  padding-bottom: 5%;
}

.row {
  margin-top: 15%;
}

#beer-img {
  max-height: 45vh;
  width: auto;
  object-fit: contain;
}

.beer-show {
  min-height: 100vh;
  background-size: cover;
  background-position: center;
  background-color: #344d5b;
  background-image: linear-gradient(rgba(0, 0, 0, 0.6), rgba(0, 0, 0, 0.6)),
    url("https://images.unsplash.com/photo-1600366060302-9fb7682b062b?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=668&q=80");
}

#arrow {
  color: white;
  font-size: 1.5rem;
  padding-top: 7%;
}
#arrow:hover {
  color: #dda15e;
}

.icons {
  color: #dda15e;
}
</style>
