<template>
  <div>
    <h1>Me</h1>
    <Description />
  </div>
</template>

<script>
import Description from "../components/Description";
export default {
  name: "Me",
  components: { Description }
};
</script>

<style scoped>
h1 {
  text-align: center;
}
</style>