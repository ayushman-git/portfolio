<template>
  <div @click="$emit('close')">
    <div class="main">
      <img :src="img" />
    </div>
    <div class="modal-bg"></div>
  </div>
</template>

<script>
export default {
  name: "ImageModal",
  props: {
    img: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.main {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 12;
}

.modal-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(5px);
}

img {
  height: 95vh;
  border-radius: 20px;
}
</style>