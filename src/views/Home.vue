<template>
  <div>
    <button v-on:click="doStuff()" class="btn btn-info mt-2">
      Sort by ABV
    </button>
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
