<template>
  <base-card>
    <base-button @click="setSelectedTab('ressource-liste')"
      >Ressources Liste</base-button
    >

    <base-button @click="setSelectedTab('add-ressource')"
      >Add Ressources</base-button
    >

    <!-- <ressource-liste></ressource-liste><AddRessource /> -->
  </base-card>
  <keep-alive> <component :is="selectedTab"></component></keep-alive>
</template>

<script>
import RessourceListe from './RessourceListe.vue';
import AddRessource from './AddRessource.vue';

export default {
  name: 'RessourcesChoice',
  components: { RessourceListe, AddRessource },
  data() {
    return {
      selectedTab: 'ressource-liste',
      storedResources: [
        {
          id: 'vuejs',
          title: 'Official Guide',
          description: 'The official Vuejs doc',
          link: 'https://vuejs.org',
        },
        {
          id: 'Laravel',
          title: 'Official documentation',
          description: 'The  Laravel documentation',
          link: 'https://laravel.com/docs/8.x',
        },
        {
          id: 'Javascript',
          title: 'Mozila developer js',
          description: 'All javascript documentation',
          link: 'https://developer.mozilla.org/fr/docs/Web/JavaScript',
        },
      ],
    };
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
      console.log(tab);
    },
    addNewRessource(title, descritopn, link) {
      const newRessource = {
        id: new Date().toISOString,
        title: title,
        descritopn: descritopn,
        link: link,
      };
      this.storedResources.unshift(newRessource);
      this.selectedTab = 'ressource-liste';
    },
    deleteRessource(id) {
      const i = this.storedResources.findIndex((rs) => rs.id === id);
      this.storedResources.splice(i, 1);
    },
  },
  provide() {
    return {
      ressources: this.storedResources,
      addNewRessource: this.addNewRessource,
      deleteRessource: this.deleteRessource,
    };
  },
};
</script>

<style scoped></style>
