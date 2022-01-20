<template>
  <h1>Formatif</h1>
  <todo-list v-bind:todos="todos"></todo-list>
  <todo v-bind:todo="todos[0]"></todo>
  <todo-edit></todo-edit>
  <project-edit v-bind:projets="projets"></project-edit>
</template>

<script>
import TodoList from "./components/TodoList.vue";
import Todo from "./components/Todo.vue";
import TodoEdit from "./components/TodoEdit.vue";
import ProjectEdit from "./components/ProjectEdit.vue";

export default {
  name: "App",
  data() {
    return {
      projets: [
        { name: "Projet 1", email: "email@projet1.com" },
        { name: "Projet 2", email: "email@projet2.com" },
        { name: "Projet 3", email: "email@projet3.com" },
      ],
      todos: [
        { title: "Todo A", project: "Project A", done: false },
        { title: "Todo B", project: "Project B", done: true },
        { title: "Todo C", project: "Project C", done: false },
      ],
    };
  },
  components: {
    TodoList,
    Todo,
    TodoEdit,
    ProjectEdit,
  },
};
</script>