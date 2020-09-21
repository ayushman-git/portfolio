<template>
  <div>
    <Hero />
  </div>
</template>

<script>
import Hero from "../components/Hero";
export default {
  name: "Home",
  components: { Hero }
};
</script>

<style scoped>
div {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>