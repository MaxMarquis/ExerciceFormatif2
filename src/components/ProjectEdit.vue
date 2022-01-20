<template>
  <h1>Projet</h1>
  <form>
    <label for="name">Nom du projet: </label>
    <input
      type="text"
      name="name"
      v-model="projet.name"
      placeholder="Nom du projet"
    /><br />
    <label for="email">Email du responsable: </label>
    <input
      type="email"
      name="email"
      v-model="projet.email"
      placeholder="exemple@email.com"
    /><br />
    <button type="button" v-on:click="ajout(name, email)">Ajouter</button>
  </form>
  <table>
    <tr>
      <th>Nom du projet</th>
      <th>Email responsable</th>
    </tr>
    <tr v-for="projet in projets" :key="projet">
      <td>{{ projet.name }}</td>
      <td>{{ projet.email }}</td>
    </tr>
  </table>
  <p>{{ errors }}</p>
</template>
<script>
export default {
  name: "ProjectEdit",
  props: ["projets"],
  data() {
    return {
      projet: { name: "", email: "" },
      errors: "",
      nameTable: [],
    };
  },
  methods: {
    ajout: function (name, email) {
      if (!name || !email) {
        return (this.errors =
          "Vous devez entrer un nom et une adresse courriel");
      }
      for (const projet of this.projets) {
        if (projet.name == this.projet.name) {
          return (this.errors = "Le nom du projet existe deja");
        }
      }
      var expNameExist = new RegExp(name, "g");
      var expNameFormat = new RegExp("^[a-zA-Z0-9]{1,5}$", "g");
      var expEmailFormat = new RegExp(
        /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/
      );
      if (expNameExist.test(this.nameTable)) {
        this.errors = "Le projet " + name + " existe déjà";
        return false;
      }
      if (expNameFormat.test(this.name)) {
        if (expEmailFormat.test(this.email)) {
          // this.projets.push(projet);
          this.errors = "";
        } else {
          this.errors = "L'adresse courriel n'est pas valide";
        }
      } else {
        this.errors =
          "Le nom ne doit pas contenir plus de 5 caractères et il ne doit pas contenir de caractères spéciaux";
      }
    },
  },
};
</script>
<style>
table {
  border: 1px black solid;
}
tr {
  border: 1px black solid;
}
</style>