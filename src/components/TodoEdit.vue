<template>
  <div>
    <input
      type="text"
      id="title"
      v-model="todo.title"
      placeholder="Titre de la tache.."
    />
    <input
      type="text"
      id="project"
      v-model="todo.project"
      placeholder="Nom du projet.."
    />
    <input type="submit" value="ajouter une tache" v-on:click="edit" />
    <p>{{ errors }}</p>
  </div>
</template>
<script>
export default {
  name: "TodoEdit",
  props: ["todos"],
  data() {
    return {
      errors: "",
      todo: { title: "", project: "" },
    };
  },
  methods: {
    edit: function () {
      // alert(`Titre de la tache: ${this.title} Projet: ${this.project} `)
      for (const todo of this.todos) {
        if (todo.project == this.todo.project) {
          return (this.errors = "Le nom du projet existe deja");
        }
        // this.todos.push(todo);
      }
    },
  },
};
</script>