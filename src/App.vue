<template>
  <div id="app">
    <navbar-main />
    <api-countries />
  </div>
</template>

<script>
import ApiCountries from "./components/ApiCountries.vue";
import NavbarMain from "./components/NavbarMain.vue";

export default {
  name: "App",
  components: {
    ApiCountries,
    NavbarMain,
},
};
</script>

<style>

</style>
