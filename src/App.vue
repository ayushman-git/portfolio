<template>
  <div id="app">
    <transition name="menu-transition">
      <Menu v-if="showMenu" class="menu-bar" v-on:close="showMenu = false" />
    </transition>
    <transition name="hidden-div-transition">
      <div @click="showMenu = false" class="hidden-div" v-if="showMenu"></div>
    </transition>
    <nav class="nav">
      <img class="logo" src="./assets/logo/logo.svg" alt="logo" />
      <img class="menu" src="./assets/icons/menu.svg" alt="menu" @click="showMenu = true" />
    </nav>
    <Home />
    <Me />
  </div>
</template>

<script>
import Home from "./section/Home";
import Me from "./section/Me";

import Menu from "./components/Menu";
export default {
  name: "App",
  components: { Home, Menu, Me },
  data() {
    return {
      showMenu: false
    };
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&display=swap");
* {
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
body {
  background-color: #1c1c1c;
  color: white;
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
  z-index: 9;
  position: fixed;
  width: 70vw;
  left: 0;
  top: 0;
  height: 100vh;
}
.menu-transition-enter-active, .menu-transition-leave-active {
  transition: all 0.3s ease-out;
}
.menu-transition-enter,
.menu-transition-leave-to {
  transform: translateX(1000px);
}
h1 {
  font-size: 72px;
}
.hidden-div-transition-active, .hidden-div-transition-leave-active {
  transition: all 0.3s ease;
}
.hidden-div-transition-enter,
.hidden-div-transition-leave-to {
  opacity: 0;
}
</style>
