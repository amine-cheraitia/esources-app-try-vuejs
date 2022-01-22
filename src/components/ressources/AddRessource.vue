<template>
  <div>
    <base-card>
      <form @submit.prevent="addRessource()">
        <div class="form-control">
          <label for="title">Title</label>
          <input type="text" name="title" id="title" v-model="title" />
        </div>
        <div class="form-control">
          <label for="description">Description</label>
          <textarea name="description" id="description" v-model="description" />
        </div>
        <div class="form-control">
          <label for="link">Link</label>
          <input type="url" name="link" id="link" v-model="link" />
        </div>
        <div>
          <base-button type="submit" @submit.prevent="addRessource()"
            >Save</base-button
          >
        </div>
      </form>
    </base-card>
    <base-dialog v-if="showError" :title="titleError">
      <template #content>
        <p>At least one input is invalid</p>
        <p>please check all the inputs</p>
      </template>
      <template #actions>
        <base-button @click="showError = false">Okay</base-button>
      </template>
    </base-dialog>
  </div>
</template>

<script>
export default {
  name: 'AddRessource',
  /* components: { BaseDialog }, */
  inject: ['addNewRessource'],
  data() {
    return {
      title: '',
      link: '',
      descritopn: '',
      showError: false,
      titleError: '',
    };
  },
  methods: {
    addRessource() {
      if (
        this.title.trim() === '' ||
        this.descritopn.trim() === '' ||
        this.link.trim() === ''
      ) {
        this.titleError = 'Invalid input';
        this.showError = true;
        return alert('veuillez rajouté');
      }
      this.addNewRessource(this.title, this.descritopn, this.link);
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
