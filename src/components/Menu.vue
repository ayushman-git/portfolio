<template>
  <nav>
    <img class="close" src="../assets/icons/close.svg" @click="$emit('close')" />
    <ul>
      <li>
        <a href="#">Me</a>
      </li>
      <li>
        <a href="#">Work</a>
      </li>
      <li>
        <a href="#">Find Me</a>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "Menu"
};
</script>

<style lang="scss" scoped>
nav {
  display: flex;
  align-items: center;
  background-color: white;
  width: 30vw;
  color: #1c1c1c;
}

ul {
  list-style-type: none;
  display: flex;
  flex-flow: column nowrap;
}

li {
  font-size: 72px;
  font-weight: 700;
  margin: 0.5em;
}

a {
  color: #1c1c1c;
  text-decoration: none;
}

a:hover {
  background-color: #1c1c1c;
  color: #59FF9C;
}
.close {
  top: 2.5em;
  right: 1.8em;
  width: 30px;
  cursor: pointer;
  position: absolute;
}
</style>