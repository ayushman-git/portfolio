<template>
  <div>
    <footer>
      <img src="../assets/logo/logo-dark.svg" alt="ayushman logo" />
      <div class="vertical-divider"></div>
      <h1>Ayushman Gupta</h1>
    </footer>
  </div>
</template>

<script>
export default {
  name: "FooterCurve"
};
</script>

<style scoped>
footer {
  height: 30vh;
  width: 60vw;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-flow: row wrap;
  background-color: white;
  user-select: none;
}

.vertical-divider {
  height: 50%;
  width: 2px;
  background-color: #1c1c1c;
}

img {
  width: clamp(42px, 8vw, 120px);
}

h1 {
  color: #1c1c1c;
  font-size: clamp(32px, 5vw, 72px);
  transition: color 0.3s ease-in-out;
}
h1:hover {
  color: #000000;
}
@media (max-width: 700px) {
  footer {
    width: 100vw;
  }
 }
</style>