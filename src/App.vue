<template>
  <the-header title="remember me"></the-header>
  <ressources-choice></ressources-choice>
  <!--   <ul>
    <ressource-liste :ressources="storedResources"></ressource-liste>
  </ul> -->
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import RessourcesChoice from './components/ressources/RessourceChoice.vue';

export default {
  components: { TheHeader, RessourcesChoice },
  data() {
    return {};
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
