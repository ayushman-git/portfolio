<template>
  <div>
    <h1>Me</h1>
    <Description class="description" />
  </div>
</template>

<script>
import Description from "../components/Description";
export default {
  name: "Me",
  components: { Description },
};
</script>

<style scoped>
div {
  display: flex;
  flex-flow: column;
  align-items: center;
  background-image: url("../assets/pattern/topography.svg");
}

h1 {
  margin-top: 1em;
  text-align: center;
}

.description {
  width: 60vw;
}
</style>