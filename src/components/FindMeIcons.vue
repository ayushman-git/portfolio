<template>
  <div
    @mouseenter="isHover = true"
    @mouseleave="isHover = false"
    class="icon-container"
    @click="onClick"
  >
    <div :class="isHover ? 'icon-circle-active' : 'icon-circle'">
      <img class="icon" :src="require(`../assets/icons/${title}.svg`)" />
      <transition name="to-right">
        <strong v-if="isHover">{{ title.charAt(0).toUpperCase() + title.slice(1) }}</strong>
      </transition>
    </div>
    <transition name="to-right">
      <div class="content-container" v-if="isHover">
        <span>{{ content }}</span>
      </div>
    </transition>
  </div>
</template>

<script>
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
  transition: all 0.2s ease-in;
}
.icon-circle-active {
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
  color: #1c1c1c;
  margin-left: 1em;
}

.to-right-enter-active,
.to-right-leave-active {
  transition: all 0.3s ease-out;
}
.to-right-enter,
.to-right-leave-to {
  opacity: 0;
  transform: translateX(-100px);
}
</style>