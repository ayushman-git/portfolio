<template>
  <nav>
    <img
      class="close"
      src="../assets/icons/close.svg"
      @click="$emit('close')"
      alt="close menu"
    />
    <ul @click="$emit('close')">
      <li>
        <a @click="openURL('me')">About Me</a>
      </li>
      <li>
        <a @click="openURL('work')">Work</a>
      </li>
      <li>
        <a @click="openURL('find-me')">Find Me</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Menu",
  methods: {
    openURL(url) {
      document.getElementById(url).scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>

<style lang="scss" scoped>
nav {
  display: flex;
  align-items: center;
  background-color: white;
  width: 40vw;
  color: #1c1c1c;
}

ul {
  list-style-type: none;
  display: flex;
  flex-flow: column nowrap;
}

li {
  font-size: clamp(40px, 5vw, 5vw);
  font-weight: 700;
  margin: 0.5em;
  cursor: pointer;
}

a {
  color: #1c1c1c;
  text-decoration: none;
}

a:hover {
  background-color: #1c1c1c;
  color: var(--primary-color);;
}
.close {
  top: 2.5em;
  right: 1.8em;
  width: 30px;
  cursor: pointer;
  position: absolute;
}

@media (max-width: 700px) {
  nav {
    width: 100vw;
  }
}
</style>