<template>
  <article>
    <h2>A little about me</h2>
    <p>
      I am a Front-End Developer with experience in building responsive websites
      while keeping the aesthetic integrity. Proficient in semantic
      <span
        ref="reactive"
        @mouseenter="reactiveHighlight"
        @mouseleave="reactiveHighlightRemove"
        >HTML, CSS, JavaScript</span
      >
      and modern frameworks like
      <span
        ref="gdesign"
        @mouseenter="gHighlight"
        @mouseleave="gHighlightRemove"
        >VueJs</span
      >
      . Always puts effort in making User Interface beautiful and practical with
      tools like
      <span
        ref="uidesign"
        @mouseenter="uiHighlight"
        @mouseleave="uiHighlightRemove"
        >Photoshop, Illustrator and Figma</span
      >
      .
    </p>
    <p>
      In my free time I work on cool projects while experimenting with new
      technologies. Currently I'm working on an astronomy discord bot and a
      chrome extension with Node, Firebase and Puppeteer.
    </p>
    <ul>
      <li>
        <img src="../assets/icons/react.svg" alt="reactjs" />
      </li>
      <li>
        <img src="../assets/icons/typescript.svg" alt="typescript" />
      </li>
      <li>
        <img src="../assets/icons/js.svg" alt="javascipt" />
      </li>
      <li>
        <img src="../assets/icons/vue.svg" alt="vuejs" />
      </li>
      <li>
        <img src="../assets/icons/python.svg" alt="python" />
      </li>
      <li>
        <img src="../assets/icons/photoshop.svg" alt="photoshop" />
      </li>
      <li>
        <img src="../assets/icons/figma.svg" alt="figma" />
      </li>
      <li>
        <a :href="pdf" download>
          <button>Resume</button>
        </a>
      </li>
    </ul>
  </article>
</template>

<script>
import { TimelineLite } from "gsap/dist/gsap";
export default {
  name: "Description",
  data() {
    return {
      pdf: require("../assets/ayushman_resume.pdf"),
    };
  },
  methods: {
    reactiveHighlight() {
      const tl = new TimelineLite();
      const { reactive } = this.$refs;
      tl.to(reactive, {
        backgroundColor: "#1a1a1a",
        color: "white",
      });
    },
    reactiveHighlightRemove() {
      const tl = new TimelineLite();
      const { reactive } = this.$refs;
      tl.to(reactive, {
        backgroundColor: "#141414",
        color: "#8d8d8d",
      });
    },
    uiHighlight() {
      const tl = new TimelineLite();
      const { uidesign } = this.$refs;
      tl.to(uidesign, {
        backgroundColor: "#1a1a1a",
        color: "white",
      });
    },
    uiHighlightRemove() {
      const tl = new TimelineLite();
      const { uidesign } = this.$refs;
      tl.to(uidesign, {
        backgroundColor: "#141414",
        color: "#8d8d8d",
      });
    },
    gHighlight() {
      const tl = new TimelineLite();
      const { gdesign } = this.$refs;
      tl.to(gdesign, {
        backgroundColor: "#1a1a1a",
        color: "white",
      });
    },
    gHighlightRemove() {
      const tl = new TimelineLite();
      const { gdesign } = this.$refs;
      tl.to(gdesign, {
        backgroundColor: "#141414",
        color: "#8d8d8d",
      });
    },
  },
};
</script>

<style scoped>
p {
  font-size: clamp(16px, 1.2vw, 1.2vw);
  line-height: 2;
  color: #9d9d9d;
}

h2 {
  font-size: clamp(24px, 3vw, 3vw);
  font-weight: 300;
  margin: 0;
}
ul {
  margin-top: clamp(3em, 4vw, 4vw);
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
  outline: none;
  font-size: 18px;
  font-weight: 900;
  background-color: white;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
}

button:hover {
  background-color: var(--primary-color);;
}

img:hover {
  filter: none;
}

span {
  background-color: #141414;
  margin: 0.3em;
  padding: 0.3em 0.7em;
  color: #8d8d8d;
}

@media (max-width: 700px) {
  img,
  button {
    height: 20px;
  }
}
</style>