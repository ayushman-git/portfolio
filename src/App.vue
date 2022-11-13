<template>
  <div id="app">
    <transition name="menu-transition">
      <Menu v-if="showMenu" class="menu-bar" @close="showMenu = false" />
    </transition>
    <transition name="hidden-div-transition">
      <div @click="showMenu = false" class="hidden-div" v-if="showMenu"></div>
    </transition>
    <svg
      version="1.1"
      id="Layer_1"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      x="0px"
      y="0px"
      viewBox="0 0 400 400"
      style="enable-background: new 0 0 400 400"
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
      style="enable-background: new 0 0 24 24"
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
    <Home id="home" class="section" />
    <Me id="me" class="section" />
    <Work
      id="work"
      v-on:emitImage="[(showImage = true), imagePreview($event)]"
    />
    <FindMe id="find-me" />
    <div class="ocean">
      <div class="wave"></div>
    </div>
    <FooterCurve class="footer" />
    <transition name="image-preview-transititon">
      <div
        v-if="showImage"
        class="image-preview-container"
        @click="[(showImage = false), (previewImageUrl = '')]"
      >
        <img :src="previewImageUrl" class="image-preview" />
      </div>
    </transition>
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
      showMenu: false,
      showImage: false,
      previewImageUrl: "",
      previewImageTitle: "",
    };
  },
  methods: {
    scrollToTop() {
      document.getElementById("app").scrollIntoView({ behavior: "smooth" });
    },
    imagePreview(e, f) {
      this.previewImageUrl = e;
      this.previewImageTitle = f;
    },
  },
  metaInfo: {
    title: "Ayushman - Portfolio",
    meta: [
      {
        name: "theme-color",
        content: "#59ff9c",
      },
      {
        name: "description",
        content: "Portfolio website of Ayushman Gupta",
      },
    ],
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&family=Source+Sans+Pro:wght@400;600;700&display=swap");
* {
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
:root {
  --primary-color: #59ff9c;
  --blue-accent-color: #11299d;
}
::selection {
  color: black;
  background-color: var(--primary-color);
}
body {
  margin: 0;
  padding: 0;
  background-color: #1c1c1c;
  color: white;
  position: relative;
  overflow-x: hidden;
  scroll-behavior: smooth;
}
.logo,
.menu {
  z-index: 1;
  margin: 2em;
  width: 30px;
  cursor: pointer;
  position: fixed;
}
.logo {
  top: 0;
  left: 0;
}
.image-preview {
  max-height: 95%;
  max-width: 95%;
  border-radius: 40px;
}
.image-preview-container {
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  position: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(4px);
  z-index: 100;
}
.image-preview-transititon-enter-active,
.image-preview-transiiton-leave-active {
  transition: all 0.3s ease;
}
.image-preview-transititon-enter,
.image-preview-transititon-leave-to {
  opacity: 0;
}
.menu {
  top: 0;
  right: 0;
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
  bottom: 29vh;
  left: 0;
}

.wave {
  background: url("./assets/pattern/wave.svg") repeat-x;
  position: absolute;
  bottom: 0;
  width: 6400px;
  height: 198px;
  animation: wave 30s cubic-bezier(0.36, 0.45, 0.63, 0.53) infinite;
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
  fill: var(--primary-color);
}
.st1 {
  fill: none;
}
.st2 {
  transition: 0.4s ease-in;
  fill: #ffffff;
}

.menu:hover .st2 {
  fill: var(--primary-color);
}

@media (max-width: 700px) {
  .section {
    height: 100%;
  }
  .ocean,
  .wave {
    display: none;
  }
}
</style>
