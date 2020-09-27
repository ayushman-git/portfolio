<template>
  <div
    @click="$emit('clicked', type)"
    :class="state ? 'type-meta-active' : 'type-meta'"
  >
    {{ type }} <img v-if="type === 'Favorites'" src="../assets/icons/star.svg" alt="favorites" />
  </div>
</template>

<script>
export default {
  name: "FilterTags",
  props: {
    type: {
      type: String,
      required: true
    },
    state: {
      type: Boolean,
      required: false,
      default: false
    }
  }
};
</script>

<style scoped>
div {
  display: flex;
}
img {
  margin-left: 0.5em;
  width: 1.2em;
}
.type-meta {
  cursor: pointer;
  margin-right: 2em;
  border-radius: 30px;
  background-color: #ffffff;
  padding: 0.5em 1.5em;
  color: #1c1c1c;
  transition: all 0.2s ease-in;
}

.type-meta:hover {
  background-color: #59ff9c;
}

.type-meta-active {
  cursor: pointer;
  margin-right: 2em;
  border-radius: 30px;
  background-color: #59ff9c;
  padding: 0.5em 1.5em;
  color: #1c1c1c;
}
</style>