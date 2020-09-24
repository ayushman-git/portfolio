<template>
  <main>
    <div class="hero-text">
      <h1 ref="greeting">Hi I'm</h1>
      <h2 ref="name">Ayushman.</h2>
      <div ref="profession" class="title-wrapper">
          <h3>Web Designer</h3>
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
import { TimelineLite } from "gsap";
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
      ease: "back.out(1.7)"
    });
    timeline.from(name, {
      y: -20,
      opacity: 0,
      duration: 0.5,
      ease: "back.out(1.7)"
    });
    timeline.from(profession, {
      y: -40,
      opacity: 0,
      duration: 0.5,
      ease: "back.out(1.7)"
    });
    tl.from(img, {
      y: -80,
      opacity: 0,
      duration: 1,
      ease: "back.out(1.7)",
      border: 0
    });
  },
  methods: {
    imagePopup() {
      const img = this.$refs.img;
      const tl = new TimelineLite();

      tl.to(img, {
        boxShadow: "0px 0px 15px 0px rgba(0,0,0,0.55)",
        scale: 1.1
      });
    },
    imagePopdown() {
      const img = this.$refs.img;
      const tl = new TimelineLite();

      tl.to(img, {
        scale: 1
      });
    }
  }
};
</script>

<style scoped>
main {
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  margin: 5em;
  width: 100%;
}

h1 {
  margin: 0;
  font-weight: 300;
  font-size: clamp(42px, 5vw, 60px);
}
h2 {
  margin: 0;
  font-size: clamp(72px, 10vw, 144px);
  font-weight: 900;
}
h3 {
  text-align: center;
  font-size: clamp(24px, 3vw, 48px);
  margin: 0;
  font-weight: 700;
}
img {
  border: clamp(6px, 1vw, 12px) solid white;
  border-radius: 50%;
  width: clamp(200px, 20vw, 320px);
}
.title-wrapper {
  margin-top: 1em;
  padding: 1em;
  width: 50%;
  background-color: white;
  color: #1c1c1c;
}
</style>