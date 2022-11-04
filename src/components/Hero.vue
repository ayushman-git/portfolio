<template>
  <main>
    <div class="hero-text">
      <h1 ref="greeting">Hi I'm</h1>
      <h2 ref="name">Ayushman.</h2>
      <div ref="profession" @click="goToMe" class="title-wrapper">
        <h3>Front-end Developer</h3>
      </div>
    </div>
    <aside class="hero-image">
      <img
        @mouseenter="imagePopup"
        @mouseleave="imagePopdown"
        ref="img"
        src="../assets/images/home-main.jpg"
        alt="Portrait photo of Ayushman"
      />
    </aside>
  </main>
</template>

<script>
import { TimelineLite } from "gsap/dist/gsap";
export default {
  name: "Hero",
  mounted() {
    const greeting = this.$refs.greeting;
    const name = this.$refs.name;
    const profession = this.$refs.profession;
    const img = this.$refs.img;

    const timeline = new TimelineLite();
    const tl = new TimelineLite();
    timeline.from(greeting, {
      y: -20,
      opacity: 0,
      duration: 0.5,
      ease: "back.out(1.7)",
    });
    timeline.from(name, {
      y: -20,
      opacity: 0,
      duration: 0.5,
      ease: "back.out(1.7)",
    });
    timeline.from(profession, {
      y: -20,
      opacity: 0,
      duration: 0.2,
      ease: "back.out(1.7)",
    });
    tl.from(img, {
      y: -80,
      opacity: 0,
      duration: 1,
      ease: "back.out(1.7)",
    });
  },
  methods: {
    imagePopup() {
      const img = this.$refs.img;
      const tl = new TimelineLite();

      tl.to(img, {
        boxShadow: "0px 0px 15px 0px rgba(0,0,0,0.55)",
        scale: 1.1,
      });
    },
    imagePopdown() {
      const img = this.$refs.img;
      const tl = new TimelineLite();

      tl.to(img, {
        scale: 1,
      });
    },
    goToMe() {
      document.getElementById("me").scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>

<style scoped>
main {
  display: flex;
  flex-flow: row wrap-reverse;
  justify-content: space-between;
  width: 100%;
}

h1 {
  margin: 0;
  font-weight: 300;
  font-size: clamp(32px, 4vw, 52px);
}
h2 {
  margin: 0;
  font-size: clamp(62px, 8vw, 140px);
  font-weight: 900;
}
h3 {
  text-align: center;
  font-size: clamp(20px, 2.8vw, 44px);
  margin: 0;
  font-weight: 700;
}
img {
  border: 10px solid white;
  border-radius: 20%;
  width: clamp(200px, 20vw, 20vw);
}
.title-wrapper {
  cursor: pointer;
  margin-top: 1.4em;
  padding: 1em;
  width: 100%;
  background-color: white;
  color: #1c1c1c;
  transition: all 0.2s ease-in-out;
  z-index: 2;
  border-radius: 20px;
}
.title-wrapper:hover {
  background-color: var(--primary-color);
}

@media (max-width: 700px) {
  main {
    justify-content: center;
    width: 100%;
  }
  img {
    margin-bottom: 2em;
  }
}
</style>