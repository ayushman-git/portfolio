<template>
  <div
    @click="$emit('clicked', type)"
    @click.middle="$emit('clicked', type)"
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
  margin-right: 1.4rem;
  border-radius: 10px;
  background-color: #ffffff;
  padding: 0.5em 1.5em;
  color: #1c1c1c;
  transition: all 0.2s ease-in;
}

.type-meta:hover {
  background-color: var(--primary-color);
}

.type-meta-active {
  cursor: pointer;
  margin-right: 1.4rem;
  border-radius: 10px;
  background-color: var(--primary-color);
  padding: 0.5em 1.5em;
  color: #1c1c1c;
}
</style>