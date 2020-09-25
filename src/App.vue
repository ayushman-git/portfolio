<template>
  <div id="app">
    <transition name="menu-transition">
      <Menu v-if="showMenu" class="menu-bar" v-on:close="showMenu = false" />
    </transition>
    <transition name="hidden-div-transition">
      <div @click="showMenu = false" class="hidden-div" v-if="showMenu"></div>
    </transition>
    <nav class="nav">
      <img
        ref="logo"
        class="logo"
        src="./assets/logo/logo.svg"
        alt="logo"
        @click="scrollToTop"
      />
      <img
        class="menu"
        src="./assets/icons/menu.svg"
        alt="menu"
        @click="showMenu = true"
      />
    </nav>
    <Home id="home" class="section" />
    <Me id="me" class="section" />
    <Work id="work" />
    <FindMe id="find-me" />
    <div class="ocean">
      <div class="wave"></div>
    </div>
    <FooterCurve class="footer" />
  </div>
</template>

<script>
import Home from "./section/Home";
import Me from "./section/Me";
import Work from "./section/Work";
import FindMe from "./section/FindMe";
import FooterCurve from "./section/FooterCurve";

import Menu from "./components/Menu";

export default {
  name: "App",
  components: { Home, Menu, Me, FindMe, FooterCurve, Work },
  data() {
    return {
      showMenu: false
    };
  },
  methods: {
    scrollToTop() {
      scrollTo(0, 0);
    }
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;600;700&display=swap");
* {
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
body {
  margin: 0;
  padding: 0;
  background-color: #1c1c1c;
  color: white;
  overflow-x: hidden;
  position: relative;
}
.logo,
.menu {
  width: 30px;
  cursor: pointer;
}
.nav {
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 2em;
  position: fixed;
}
.menu-bar {
  z-index: 10;
  position: fixed;
  right: 0;
  top: 0;
  height: 100vh;
}
.hidden-div {
  backdrop-filter: blur(3px);
  z-index: 5;
  position: fixed;
  width: 100%;
  left: 0;
  top: 0;
  height: 100vh;
}
.menu-transition-enter-active,
.menu-transition-leave-active {
  transition: all 0.3s ease-out;
}
.menu-transition-enter,
.menu-transition-leave-to {
  transform: translateX(80vw);
}
h1 {
  font-size: 72px;
}
.hidden-div-transition-active,
.hidden-div-transition-leave-active {
  transition: all 0.3s ease;
}
.hidden-div-transition-enter,
.hidden-div-transition-leave-to {
  opacity: 0;
}
.section {
  height: 100vh;
  width: 100%;
}
.footer {
  display: flex;
  justify-content: center;
  background-color: white;
}

.ocean { 
  height: 100px;
  width:100%;
  position:absolute;
  bottom:20vh;
  left:0;
}

.wave {
  background: url("./assets/pattern/wave.svg") repeat-x; 
  position: absolute;
  bottom: 0;
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
