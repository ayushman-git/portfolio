<template>
  <article>
    <h2>A little about me</h2>
    <p>
      Hi I'm Ayushman. I love creating things and making them look pretty. I
      design and create static as well as
      <span
        ref="reactive"
        @mouseenter="reactiveHighlight"
        @mouseleave="reactiveHighlightRemove"
        >reactive web apps</span
      >
      with the help of vue or javascript. I've been always fascinated with
      technology ever since I was a kid. I used to create mini-web pages, fiddle
      with existing websites to make them look ridiculous. It was in my
      graduation days that I dived deep into web development and programming in
      general. Being a programmer and having a craving for creation opens up
      door to lot of possibilities.
    </p>

    <p>
      Besides programming I also love designing. I try to design creative
      <span
        ref="uidesign"
        @mouseenter="uiHighlight"
        @mouseleave="uiHighlightRemove"
        >UI designs</span
      >
      for my projects with figma. In my free time I create
      <span
        ref="gdesign"
        @mouseenter="gHighlight"
        @mouseleave="gHighlightRemove"
        >graphic designs</span
      >
      with photoshop. If you like my work you can hire me.
    </p>
    <ul>
      <li>
        <img src="../assets/icons/js.svg" alt="javascipt" />
      </li>
      <li>
        <img src="../assets/icons/vue.svg" alt="vuejs" />
      </li>
       <li>
        <img src="../assets/icons/nodejs.svg" alt="nodejs" />
      </li>
      <li>
        <img src="../assets/icons/photoshop.svg" alt="photoshop" />
      </li>
      <li>
        <img src="../assets/icons/illustrator.svg" alt="illustrator" />
      </li>
      <li>
        <img src="../assets/icons/figma.svg" alt="figma" />
      </li>
      <li>
        <button>CV</button>
      </li>
    </ul>
  </article>
</template>

<script>
import { TimelineLite } from "gsap/dist/gsap";
export default {
  name: "Description",
  methods: {
    reactiveHighlight() {
      const tl = new TimelineLite();
      const { reactive } = this.$refs;
      tl.to(reactive, {
        backgroundColor: "#1a1a1a",
        color: "white"
      });
    },
    reactiveHighlightRemove() {
      const tl = new TimelineLite();
      const { reactive } = this.$refs;
      tl.to(reactive, {
        backgroundColor: "#141414",
        color: "#8d8d8d"
      });
    },
    uiHighlight() {
      const tl = new TimelineLite();
      const { uidesign } = this.$refs;
      tl.to(uidesign, {
        backgroundColor: "#1a1a1a",
        color: "white"
      });
    },
    uiHighlightRemove() {
      const tl = new TimelineLite();
      const { uidesign } = this.$refs;
      tl.to(uidesign, {
        backgroundColor: "#141414",
        color: "#8d8d8d"
      });
    },
    gHighlight() {
      const tl = new TimelineLite();
      const { gdesign } = this.$refs;
      tl.to(gdesign, {
        backgroundColor: "#1a1a1a",
        color: "white"
      });
    },
    gHighlightRemove() {
      const tl = new TimelineLite();
      const { gdesign } = this.$refs;
      tl.to(gdesign, {
        backgroundColor: "#141414",
        color: "#8d8d8d"
      });
    }
  }
};
</script>

<style scoped>
p {
  font-size: clamp(16px, 1.04vw, 1.04vw);
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
  font-size: 18px;
  font-weight: 900;
  background-color: white;
  cursor: pointer;
  transition: background-color 0.2s ease-in-out;
}

button:hover {
  background-color: #59ff9c;
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