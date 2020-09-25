<template>
  <div class="main-container">
    <h1>Find Me</h1>
    <div class="find-me-container">
      <img
      ref="img"
        src="../assets/images/home-main.jpg"
        alt="Portrait photo of Ayushman"
        @mouseenter="imagePopup"
        @mouseleave="imagePopdown"
      />
      <div class="icons">
        <FindMeIcons title="email" content="ayushman1998.1998@gmail.com" />
        <FindMeIcons
          title="instagram"
          content="ayushman_fx"
          link="http://instagram.com/ayushman_fx"
        />
        <FindMeIcons
          title="dribbble"
          content="Duoro"
          link="https://dribbble.com/Duoro"
        />
        <FindMeIcons
          title="behance"
          content="Ayushman"
          link="https://www.behance.net/duoro"
        />
        <FindMeIcons
          title="500px"
          content="Ayushman"
          link="https://500px.com/p/duoro?view=photos"
        />
        <FindMeIcons
          title="deviantart"
          content="Duoro"
          link="https://www.deviantart.com/duoro"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { TimelineLite } from "gsap";

import FindMeIcons from "../components/FindMeIcons";
export default {
  name: "FindMe",
  components: {
    FindMeIcons
  },
  methods: {
    imagePopup() {
      const img = this.$refs.img;
      const tl = new TimelineLite();

      tl.to(img, {
        boxShadow: "0px 0px 15px 0px rgba(0,0,0,0.55)",
        scale: 1.1
      });
    },
    imagePopdown() {
      const img = this.$refs.img;
      const tl = new TimelineLite();

      tl.to(img, {
        scale: 1
      });
    }
  }
};
</script>

<style scoped>
.main-container {
  padding-bottom: 20em;
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
  border: clamp(6px, 1vw, 12px) solid white;
  border-radius: 50%;
  width: clamp(200px, 20vw, 320px);
}
.find-me-container {
  width: 80vw;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
  align-items: center;
}
.icons {
  margin-left: 7em;
  flex: 0 1 40%;
}

.icons * {
  margin-top: 1em;
}

.ocean { 
  height: 5%;
  width:100%;
  position:absolute;
  bottom:0;
  left:0;
  background: #1c1c1c;
}

.wave {
  background: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/85486/wave.svg) repeat-x; 
  position: absolute;
  top: -198px;
  width: 6400px;
  height: 198px;
  animation: wave 7s cubic-bezier( 0.36, 0.45, 0.63, 0.53) infinite;
  transform: translate3d(0, 0, 0);
}

@keyframes wave {
  0% {
    margin-left: 0;
  }
  100% {
    margin-left: -1600px;
  }
}
</style>