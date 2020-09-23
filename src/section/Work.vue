<template>
  <div>
    <h1>Work</h1>
    <ProjectModule class="module" />
  </div>
</template>

<script>
import ProjectModule from "../components/ProjectModule";
export default {
  name: "Work",
  components: {
    ProjectModule
  }
};
</script>
<style scoped>
div {
  display: flex;
  flex-flow: column;
  align-items: center;
  background: url("../assets/pattern/graph-paper.svg");
}

.module {
  margin-bottom: 10em;
}
</style>