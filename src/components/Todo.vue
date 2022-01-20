<template>
  <div>
    {{ todo.title }}
    {{ todo.project }}
  </div>
</template>
<script>
export default {
  name: "Todo",
  props: ["todo"],
};
</script>