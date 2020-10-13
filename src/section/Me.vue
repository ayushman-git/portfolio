<template>
  <div>
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
  justify-content: center;
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

@media (max-width: 700px) {
  div {
    padding: 4em 0em;
  }
  .description {
    text-align: justify;
    width: 90vw;
  }
}
</style>