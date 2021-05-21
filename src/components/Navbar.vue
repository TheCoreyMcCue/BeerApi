<template>
  <b-navbar
    class="sticky-top bg-dark"
    toggleable="lg"
    type="dark"
    variant="info"
  >
    <b-navbar-brand href="/"
      ><img src="../assets/logo.png" alt="" width="38" height="33" />
      BeerMe</b-navbar-brand
    >

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#/">Home</b-nav-item>
        <b-nav-item href="#/random">Random Beer</b-nav-item>
        <b-nav-item href="#/about">About</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto"> </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
import { Component, Vue } from "vue-property-decorator";

@Component
export default class Navbar extends Vue {}
</script>
