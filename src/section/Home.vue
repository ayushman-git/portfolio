<template>
  <div>
    <Hero class="hero" />
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
.hero {
  width: 80vw;
}
</style>