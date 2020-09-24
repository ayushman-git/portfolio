<template>
  <article>
    <h2>A lil' about Me</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. In porttitor tortor non elit tempus, eget accumsan diam gravida. Nulla imperdiet ultricies mi at ultrices. Aenean pretium, lectus in pulvinar vulputate, ex magna tincidunt urna, tempor eleifend ex libero ac sapien. Ut eu imperdiet tellus, in ultricies nisl. Nam at consequat purus, at auctor arcu. Mauris eros velit, fermentum vel dolor sed, ultricies dictum metus. Vestibulum faucibus massa dui. Aenean sagittis mauris non nunc ullamcorper finibus sed a nisi. Aenean mi ipsum, aliquam tincidunt facilisis in, tristique nec felis.</p>
    <ul>
      <li>
        <img src="../assets/icons/js.svg" />
      </li>
      <li>
        <img src="../assets/icons/vue.svg" />
      </li>
      <li>
        <img src="../assets/icons/photoshop.svg" />
      </li>
      <li>
        <img src="../assets/icons/illustrator.svg" />
      </li>
      <li>
        <img src="../assets/icons/figma.svg" />
      </li>
      <li>
        <button>CV</button>
      </li>
    </ul>
  </article>
</template>

<script>
export default {
  name: "Description"
};
</script>

<style scoped>
p {
  line-height: 2;
  color: #9d9d9d;
}

h2 {
  font-size: clamp(24px, 3vw, 42px);
  font-weight: 300;
  margin: 0;
}
ul {
  margin-top: 3em;
  list-style-type: none;
  display: flex;
  justify-content: space-around;
}
img {
  height: 30px;
  filter: grayscale();
  transition: filter 0.2s ease-in-out;
}
button {
  height: 30px;
  border: none;
  font-size: 18px;
  font-weight: 900;
  background-color: white;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
}

button:hover {
  background-color: #59FF9C;
}

img:hover {
  filter: none;
}
</style>