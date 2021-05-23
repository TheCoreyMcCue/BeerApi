<template>
  <div id="footer" class="container">
    <div class="hr"></div>
    <div class="container">
      <div class="d-flex justify-content-center footer-links">
        <a class="footer-link" href="/">home</a>
        <a class="footer-link" href="/#/random">random beer</a>
        <a class="footer-link" href="/#/about">about</a>
      </div>
      <p>
        <img class="icon" src="../assets/logo.png" />
        <span>
          <strong>&copy; 2021 BeerMe</strong>. A full-stack Vue.js demo app by
          Corey McCue
        </span>
      </p>
    </div>
  </div>
</template>

<script>
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Navbar extends Vue {}
</script>
<style scoped>
#footer {
  margin-bottom: 3em;
}

#footer .icon {
  height: 3em;
  display: inline-block;
  padding-right: 1rem;
  /* margin-bottom: -6px; */
}

.hr {
  border-bottom: 1px solid #dbdbdb;
  margin: 3em 0;
}

#footer p {
  font-size: 15px;
  color: #767676 !important;
}

.footer-link {
  margin-inline: 8%;
}
.footer-links {
  margin-bottom: 3%;
}
</style>
