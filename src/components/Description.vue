<template>
  <article>
    <h2>A little about me</h2>
    <!-- <p>
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
    </p> -->
    <p>
      I'm a software engineer with a computer science background. I started my career as a front-end developer in an
      ed-tech startup and transitioned into a full-stack role for an agri-tech company. Working in startups gave me the
      opportunity to wear multiple hats and be involved in the entire process of creating a feature from its conception
      to reality.
    </p>
    <p>
      I mostly use Javascript for my projects. But for the past year, I've been using Typescript cause I love the type
      safety and IDE support it provides. React and Next are my daily drivers for front-end undertakings though I
      frequently dabble with new frameworks like svelte, remix etc. Being in react ecosystem helped me to pick up mobile
      development quite easily. React Native is my go-to framework for mobile development because of its lucid docs.
      Besides these, I always explore new frameworks and technologies like deno, bun, nest etc.
    </p>
    <p>
      I'm a big nerd for astronomy, ancient history and technology. I keep my brain's neurons active by reading books
      and listening to podcasts about these topics. Besides these, I like to draw, speedcubing, write tech articles and
      play video games.
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
  font-size: clamp(16px, 1.15vw, 1.15vw);
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
  background-color: var(--primary-color);
  ;
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