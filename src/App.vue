<template>
  <div id="app">
    <transition name="menu-transition">
      <Menu v-if="showMenu" class="menu-bar" v-on:close="showMenu = false" />
    </transition>
    <transition name="hidden-div-transition">
      <div @click="showMenu = false" class="hidden-div" v-if="showMenu"></div>
    </transition>
    <nav class="nav">
      <svg
        version="1.1"
        id="Layer_1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        x="0px"
        y="0px"
        viewBox="0 0 400 400"
        style="enable-background:new 0 0 400 400;"
        xml:space="preserve"
        class="logo"
        @click="scrollToTop"
      >
        <g>
          <path
            class="st0"
            d="M308,89.9v234h-35.4v-36.6c-21.6,22.8-52.2,36.6-85.8,36.6c-66.6,0-120-54-120-120c0-66,53.4-120,120-120
		c33.6,0,64.2,13.8,85.8,36.6V89.9H308z M272.6,204.5c0-47.4-38.4-85.8-84.6-85.8c-48,0-86.4,38.4-86.4,85.8
		c0,46.8,38.4,85.2,86.4,85.2C234.2,289.7,272.6,251.3,272.6,204.5z"
          />
        </g>
      </svg>
      <svg
        version="1.1"
        id="Layer_1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        x="0px"
        y="0px"
        viewBox="0 0 24 24"
        style="enable-background:new 0 0 24 24;"
        xml:space="preserve"
        class="menu"
        @click="showMenu = true"
      >
        <path class="st1" d="M0,0h24v24H0V0z" />
        <path
          class="st2"
          d="M3,18h18v-2H3V18z M3,13h18v-2H3V13z M3,6v2h18V6H3z"
        />
      </svg>
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
  width: 100%;
  position: absolute;
  bottom: 20vh;
  left: 0;
}

.wave {
  background: url("./assets/pattern/wave.svg") repeat-x;
  position: absolute;
  bottom: 0;
  width: 6400px;
  height: 220px;
  animation: wave 24s cubic-bezier(0.36, 0.45, 0.63, 0.53) infinite;
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

.st0 {
  fill: #ffffff;
  transition: 0.4s ease-in;
}

.logo:hover .st0 {
  fill: #59ff9c;
}
.st1 {
  fill: none;
}
.st2 {
  transition: 0.4s ease-in;
  fill: #ffffff;
}

.menu:hover .st2 {
  fill: #59ff9c;
}
</style>
