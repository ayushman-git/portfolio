<template>
  <div ref="maincontainer" class="icon-container" @click="onClick">
    <div
      :class="isHover ? 'icon-circle-active' : 'icon-circle'"
      @mouseenter="[containerAnimation(), (isHover = true)]"
      @mouseleave="isHover = false"
    >
      <img class="icon" :src="require(`../assets/icons/${title}.svg`)" :alt="title" />
      <strong v-if="isHover">{{
        title.charAt(0).toUpperCase() + title.slice(1)
      }}</strong>
    </div>
    <transition v-on:enter="contentAnimation">
      <div ref="contentdiv" class="content-container" v-if="isHover">
        <span>{{ content }}</span>
      </div>
    </transition>
  </div>
</template>

<script>
import { TimelineLite } from "gsap/dist/gsap";
export default {
  name: "FindMeIcons",
  props: {
    title: {
      type: String,
      required: true
    },
    content: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: false
    }
  },
  data() {
    return {
      isHover: false
    };
  },
  methods: {
    onClick() {
      if (this.link) {
        window.open(this.link, "_blank", "noopener");
      }
    },
    contentAnimation() {
      const { contentdiv } = this.$refs;
      const tl = new TimelineLite();

      tl.from(contentdiv, {
        x: -50,
        opacity: 0,
        duration: 0.2,
        ease: "circ.out"
      });
    },
    containerAnimation() {
      const { maincontainer } = this.$refs;
      const tl = new TimelineLite();
      tl.from(maincontainer, {
        width: "40%",
        duration: 0.5
      });
    }
  }
};
</script>

<style scoped>
.icon-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
}
.icon {
  width: 24px;
}
.icon-circle {
  display: flex;
  justify-content: center;
  border-radius: 50%;
  width: 40px;
  background-color: white;
  height: 40px;
}
.icon-circle-active {
  z-index: 2;
  display: flex;
  justify-content: flex-start;
  padding-left: 8px;
  align-items: center;
  border-radius: 50px 0px 0px 50px;
  width: 40%;
  background-color: #59ff9c;
  height: 40px;
}
.content-container {
  width: 70%;
  color: #1c1c1c;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 0px 50px 50px 0px;
  margin-left: 5px;
  height: 40px;
  background-color: #ffffff;
}

strong {
  font-size: clamp(14px, 1.1vw, 24px);
  color: #1c1c1c;
  margin-left: 1em;
}

span {
  font-size: clamp(12px, 1vw, 20px);
}
</style>