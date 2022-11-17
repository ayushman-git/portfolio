<template>
  <article ref="container" class="project-container">
    <div class="project-container-sub-module">
      <header :style="{ 'margin-bottom': content ? '0em' : '3.8em' }">
        <div class="title-type">
          <h1 @click="readMore">{{ projectName }}</h1>
          <!-- <div class="type-meta">{{ type }}</div> -->
        </div>
        <div class="custom-icons">
          <a v-for="(link, platform) in preview" :key="platform.index" :href="link" target="_blank" rel="noopener">
            <img class="preview-platform-icons" :src="require(`../assets/icons/${platform}.svg`)"
              :alt="`link for ${platform}`" />
          </a>
        </div>
      </header>
      <p v-if="content">
        {{ content }} <br />
        <span class="read-more" @click="readMore">Read more →</span>
      </p>

      <!-- <button v-if="read" @click="readMore" class="more">
        <span v-if="type === 'Graphic Design'">
          Watch
          <svg xmlns="http://www.w3.org/2000/svg" height="18" viewBox="0 0 24 24" width="18">
            <path d="M0 0h24v24H0z" fill="none" />
            <path d="M4.2,0.2v23.6L22.8,12L4.2,0.2z" />
          </svg></span>
        <span v-else> Read More </span>
      </button> -->
    </div>
    <img ref="image" class="cover-image" :src="coverImage" :alt="`Screenshot of ${projectName}`" @click="emitImage" />

  </article>
</template>

<script>
export default {
  name: "ProjectModule",
  props: {
    title: {
      type: String,
      required: true,
    },
    content: {
      content: {
        type: String,
        required: false,
      },
    },
    preview: {
      type: Object,
      required: true,
    },
    coverImage: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      required: true,
    },
    read: {
      type: String,
      required: false,
    },
  },
  data() {
    return {
      imageBounds: null,
      containerBounds: null,
    }
  },

  mounted() {
    const { image, container } = this.$refs;
    this.addMouseHoverEventListeners(image, this.rotateToMouse, true);
    this.addMouseHoverEventListeners(container, this.rotateToMouseContainer);
  },

  computed: {
    projectName() {
      let projectName = this.title;
      projectName = projectName.charAt(0).toUpperCase() + projectName.slice(1);
      projectName = projectName.replace(/_/g, " ");
      return projectName;
    },
  },
  methods: {
    addMouseHoverEventListeners(element, rotatingFunc, isImage) {
      element.addEventListener('mouseenter', () => {
        if (isImage) {
          this.imageBounds = element.getBoundingClientRect();
        } else {
          this.containerBounds = element.getBoundingClientRect();
        }
        document.addEventListener('mousemove', rotatingFunc);
      });

      element.addEventListener('mouseleave', () => {
        document.removeEventListener('mousemove', rotatingFunc);
        element.style.transform = '';
        element.style.background = '';
      });
    },
    readMore() {
      window.open(this.read, "_blank", "noopener");
    },
    emitImage() {
      this.$emit("emitImage", this.coverImage);
    },
    rotateToMouse(e) {
      const { clientX, clientY } = e;
      const leftX = clientX - this.imageBounds.x;
      const topY = clientY - this.imageBounds.y;
      const center = {
        x: leftX - this.imageBounds.width / 2,
        y: topY - this.imageBounds.height / 2
      }
      const distance = Math.sqrt(center.x ** 2 + center.y ** 2);

      this.$refs.image.style.transform = `
    scale3d(1.11, 1.11, 1.11)
    rotate3d(
      ${center.y / 100},
      ${-center.x / 100},
      0,
      ${Math.log(distance)}deg
    )
  `;
    },
    rotateToMouseContainer(e) {
      const { clientX, clientY } = e;
      const leftX = clientX - this.containerBounds.x;
      const topY = clientY - this.containerBounds.y;
      const center = {
        x: leftX - this.containerBounds.width / 2,
        y: topY - this.containerBounds.height / 2
      }
      const distance = Math.sqrt(center.x ** 2 + center.y ** 2);

      this.$refs.container.style.transform = `
    rotate3d(
      ${center.y / 200},
      ${-center.x / 200},
      0,
      ${Math.log(distance) * 0.5}deg
    )
  `;
    }
  },
};
</script>

<style scoped>
.project-container {
  display: flex;
  flex-flow: column nowrap;
  background-color: white;
  border-radius: 40px;
  color: #1c1c1c;
  width: 60vw;
  padding-bottom: 4rem;
  perspective: 1500px;
  max-width: 1000px;
  /* transform: rotate3d(0); */
}

.project-container:hover {
  transition-duration: 150ms;
}

.project-container-sub-module {
  padding: 2em 2em 0em 2em;
}

header {
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: space-between;
}

.title-type > h1 {
  display: flex;
  align-items: center;
  flex-flow: row nowrap;
  cursor: pointer;
  user-select: none;
  transition: all 250ms ease-in-out;
}
.title-type > h1:hover {
  color: var(--blue-accent-color);
}

h1 {
  font-size: clamp(20px, 4vw, 4vw);
  margin: 0;
  color: #1c1c1c;
}

p {
  white-space: pre-line;
  padding-bottom: 2em;
  font-size: clamp(16px, 1.2vw, 1.2vw);
  font-family: "Source Sans Pro", sans-serif;
  line-height: 1.6;
  color: #797979;
}

.cover-image {
  width: 100%;
  transform: scale(1.1);
  border-radius: 40px;
  cursor: pointer;
  box-shadow:
    0 2.8px 2.2px rgba(0, 0, 0, 0.034),
    0 6.7px 5.3px rgba(0, 0, 0, 0.048),
    0 12.5px 10px rgba(0, 0, 0, 0.06),
    0 22.3px 17.9px rgba(0, 0, 0, 0.072),
    0 41.8px 33.4px rgba(0, 0, 0, 0.086),
    0 100px 80px rgba(0, 0, 0, 0.12);
  transition-duration: 300ms;
  transition-property: transform, box-shadow;
  transition-timing-function: ease-out;
  /* transform: rotate3d(0); */
}

.cover-image:hover {
  transition-duration: 150ms;
  box-shadow:
    0 4px 3.2px rgba(0, 0, 0, 0.034),
    0 7.7px 6.3px rgba(0, 0, 0, 0.048),
    0 13.5px 12px rgba(0, 0, 0, 0.06),
    0 25.3px 19px rgba(0, 0, 0, 0.072),
    0 45.8px 35px rgba(0, 0, 0, 0.086),
    0 130px 90px rgba(0, 0, 0, 0.12);
}

.type-meta {
  margin-left: 2em;
  border-radius: 10px;
  background-color: #e8e8e8;
  padding: 0.5em 1.5em;
  color: #939393;
  user-select: none;
  transition: all 0.2s ease-in-out;
}

.type-meta:hover {
  color: #939393;
  background-color: #d8d8d8;
}

.more {
  cursor: pointer;
  position: absolute;
  z-index: 10;
  font-size: 1.4em;
  font-weight: 600;
  background-color: rgba(255, 255, 255, 0.6);
  color: #1c1c1c;
  border-radius: 15px;
  border: 4px solid #1c1c1c;
  margin-bottom: 6rem;
  padding: 0.5em;
  bottom: 0;
  left: 50%;
  backdrop-filter: blur(5px);
  transform: translate(-50%, 50%);
  transition: all 0.2s ease-in-out;
  outline: none;
}

.more:hover {
  background-color: #1c1c1c;
  color: white;
  border: 4px solid white;
}

.more:hover span {
  fill: #ffffff;
}

.more span {
  display: flex;
  align-items: center;
}

.more span svg {
  margin-left: 0.2em;
}

.preview-platform-icons {
  width: 30px;
  font-weight: 600;
  margin-left: 2em;
  opacity: 0.6;
  transition: opacity 0.2s ease-in-out;
}

.preview-platform-icons:hover {
  opacity: 1;
}

.more span {
  display: flex;
  justify-content: center;
  fill: #1c1c1c;
  transition: all 0.2s ease-in-out;
}

.read-more {
  cursor: pointer;
  display: inline-block;
  font-size: clamp(16px, 1.2vw, 1.2vw);
  font-family: "Source Sans Pro", sans-serif;
  line-height: 1.6;
  margin-top: 0.8rem;
  transition: all 250ms ease-in-out;
}

.read-more:hover {
  transform: translateX(6px);
  color: var(--blue-accent-color);
}

@media (max-width: 700px) {
  .project-container {
    padding: 1em 1em 2em 1em;
    width: 90vw;
    border-radius: 15px;
  }

  .project-container-sub-module {
    padding: 1em 1em 0em 1em;
  }

  .cover-image {
    border-radius: 5px;
  }

  .preview-platform-icons {
    width: 20px;
  }

  .type-meta {
    margin-left: 1em;
    border-radius: 30px;
    background-color: #e8e8e8;
    padding: 0.5em 1.5em;
    color: #939393;
  }

  .custom-icons {
    display: none;
  }
}
</style>