<template>
  <div>
    <h2>Formulaire d'utilisateur</h2>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="name">Nom :</label>
        <input type="text" id="name" v-model="name" />
        <span v-if="errors.name">{{ errors.name }}</span>
      </div>
      <div>
        <label for="email">Email :</label>
        <input type="email" id="email" v-model="email" />
        <span v-if="errors.email">{{ errors.email }}</span>
      </div>
      <div>
        <label for="phone">Téléphone :</label>
        <input type="tel" id="phone" v-model="phone" />
        <span v-if="errors.phone">{{ errors.phone }}</span>
      </div>
      <button type="submit">Soumettre</button>
      <div v-if="successMessage">{{ successMessage }}</div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      errors: {},
      successMessage: ''
    };
  },
  methods: {
    handleSubmit() {
      this.errors = {};
      if (!this.name) this.errors.name = 'Le nom est requis';
      if (!this.email) this.errors.email = 'L\'email est requis';
      if (!this.phone) this.errors.phone = 'Le téléphone est requis';
      if (Object.keys(this.errors).length === 0) {
        this.successMessage = 'Formulaire soumis avec succès';
        // Réinitialiser le formulaire
        this.name = '';
        this.email = '';
        this.phone = '';
      }
    }
  }
};
</script>

<style scoped>
form div {
  margin-bottom: 10px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 100%;
}

span {
  color: red;
  font-size: 0.9em;
}

button {
  padding: 10px 15px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
