<template>
  <ul>
    <ressource
      v-for="res in ressources"
      :key="res.id"
      :link="res.link"
      :title="res.title"
      :description="res.description"
      :id="res.id"
    ></ressource>
  </ul>
</template>

<script>
import ressource from './Ressource.vue';
export default {
  name: 'RessourceListe',
  components: { ressource },
  inject: ['ressources'],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
