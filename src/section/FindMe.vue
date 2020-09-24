<template>
  <div class="main-container">
    <h1>Find Me</h1>
    <div class="find-me-container">
      <img src="../assets/images/home-main.jpg" alt="Portrait photo of Ayushman" />
      <div class="icons">
        <FindMeIcons title="email" content="ayushman1998.1998@gmail.com" />
        <FindMeIcons title="instagram" content="ayushman_fx" link="http://instagram.com/ayushman_fx" />
        <FindMeIcons title="dribbble" content="Ayushman" link="https://dribbble.com/Duoro" />
        <FindMeIcons title="behance" content="Ayushman" link="https://www.behance.net/duoro" />
        <FindMeIcons title="500px" content="Ayushman" link="https://500px.com/p/duoro?view=photos" />
        <FindMeIcons title="deviantart" content="Duoro" link="https://www.deviantart.com/duoro" />
      </div>
    </div>
  </div>
</template>

<script>
import FindMeIcons from "../components/FindMeIcons";
export default {
  name: "FindMe",
  components: {
    FindMeIcons
  }
};
</script>

<style scoped>
.main-container {
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  background: url("../assets/pattern/tic-tac-toe.svg");
}
h1 {
  margin-top: 1em;
  text-align: center;
}
img {
  border: 12px solid white;
  border-radius: 50%;
  width: 300px;
  height: 300px;
}
.find-me-container {
  width: 80vw;
  display: flex;
  flex-flow: row wrap;
  align-items: center;
}
.icons {
  margin-left: 5em;
  flex: 0 1 40%;
}

.icons * {
  margin-top: 1em;
}
</style>