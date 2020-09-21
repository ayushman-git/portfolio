<template>
  <main>
    <div class="hero-text">
      <h1>Hi I'm</h1>
      <h2>Ayushman.</h2>
      <div class="title-wrapper">
        <h3>Web Designer</h3>
      </div>
    </div>
    <aside class="hero-image">
      <img src="../assets/images/home-main.jpg" alt="Portrait photo of Ayushman" />
    </aside>
  </main>
</template>

<script>
export default {
  name: "Hero"
};
</script>

<style scoped>
main {
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  margin: 5em;
  width: 100%;
}

h1 {
  margin: 0;
  font-weight: 300;
  font-size: 60px;
}
h2 {
  margin: 0;
  font-size: 144px;
  font-weight: 900;
}
h3 {
  text-align: center;
  font-size: 48px;
  margin: 0;
  font-weight: 700;
}
img {
  border: 12px solid white;
  border-radius: 50%;
  width: 300px;
  height: 300px;
}
.title-wrapper {
  margin-top: 1em;
  padding: 1em;
  width: 50%;
  background-color: white;
  color: #1c1c1c;
}
</style>