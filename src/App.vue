<template>
  <div id="app">
    <TaskListOrganism />
  </div>
</template>

<script>
import TaskListOrganism from "./components/organisms/TaskListOrganism.vue";

export default {
  name: "App",
  components: {
    TaskListOrganism,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
