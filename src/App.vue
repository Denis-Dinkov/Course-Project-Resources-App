<template>
  <the-header title="RembemberMe"></the-header>
  <the-resources></the-resources>

</template>

<script>
import TheHeader from "./components/layots/TheHeader.vue";
import TheResources from "./components/learning-recources/TheResources.vue";
export default {
  components: {
    TheHeader,
    TheResources
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: "Roboto", sans-serif;
}

body {
  margin: 0;
}
</style>
