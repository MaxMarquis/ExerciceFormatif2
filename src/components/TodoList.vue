<template>
  <div>
    <ul>
      <li v-for="todo in todos" :key="todo.project">{{ todo.project }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "TodoList",
  props: ["todos"],
};
</script>