<template>
  <div id="app" class="container">
    <ToDoApp/>
  </div>
</template>
<script>
import ToDoApp from "./components/ToDoApp.vue";

export default {
  components: {
    ToDoApp
  }
};
</script>
<style>
  .container {
    display: flex;
    justify-content: center;
    width: 100%;
  }
</style>
