<template>
  <div>
    <div class="banner">
      <div class="container">
        <h1>
          <strong>BeerMe</strong>
        </h1>
        <p>The only online beer site you'll ever need.</p>
        <a @click="sorted = !sorted" class="btn btn-info" href="#"
          >Sort Beers by ABV %</a
        >
      </div>
    </div>
    <SortedAbv v-if="sorted" />
    <BeerList v-else />
  </div>
</template>
<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import BeerList from "../components/BeerList.vue";
import SortedAbv from "../components/SortedAbv.vue";

export default {
  components: {
    BeerList,
    SortedAbv,
  },
  name: "Home",
  props: {},
  data() {
    return {
      sorted: false,
    };
  },
  methods: {
    doStuff() {
      return (this.sorted = true);
    },
  },
};
</script>
<style scoped>
.banner {
  background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    url("https://images.unsplash.com/photo-1589711428920-bf084b80e0bd?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2850&q=80");
  background-size: cover;
  background-position: center;
  padding: 150px 0;
}

.banner h1 {
  margin: 0;
  color: white;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
  font-size: 32px;
  font-weight: bold;
}

.banner p {
  font-size: 20px;
  color: white;
  opacity: 0.85;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
}
</style>
