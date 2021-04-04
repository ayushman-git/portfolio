<template>
  <article class="project-container">
    <header>
      <div class="title-type">
        <h1>{{ projectName }}</h1>
        <div class="type-meta">{{ type }}</div>
      </div>
      <div class="custom-icons">
        <a
          v-for="(link, platform) in preview"
          :key="platform.index"
          :href="link"
          target="_blank"
          rel="noopener"
        >
          <img
            class="preview-platform-icons"
            :src="require(`../assets/icons/${platform}.svg`)"
            :alt="`link for ${platform}`"
          />
        </a>
      </div>
    </header>
    <p v-if="content">
      {{ content }}
    </p>
    <img
      class="cover-image"
      :src="coverImage"
      :alt="`Screenshot of ${projectName}`"
      @click="emitImage"
    />

    <button v-if="read" @click="readMore" class="more">
      <span v-if="type === 'Graphic Design'">
        Watch
        <svg
          xmlns="http://www.w3.org/2000/svg"
          height="18"
          viewBox="0 0 24 24"
          width="18"
        >
          <path d="M0 0h24v24H0z" fill="none" />
          <path d="M4.2,0.2v23.6L22.8,12L4.2,0.2z" /></svg
      ></span>
      <span v-else> Read More </span>
    </button>
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

  computed: {
    projectName() {
      let projectName = this.title;
      projectName = projectName.charAt(0).toUpperCase() + projectName.slice(1);
      projectName = projectName.replace(/_/g, " ");
      return projectName;
    },
  },
  methods: {
    readMore() {
      window.open(this.read, "_blank", "noopener");
    },
    emitImage() {
      this.$emit("emitImage", this.coverImage);
    },
  },
};
</script>

<style scoped>
.project-container {
  position: relative;
  display: flex;
  flex-flow: column nowrap;
  padding: 2em 2em 4em 2em;
  background-color: white;
  border-radius: 40px;
  color: #1c1c1c;
  width: 70vw;
  max-width: 1000px;
}

header {
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: space-between;
}

.title-type {
  display: flex;
  align-items: center;
  flex-flow: row nowrap;
}

h1 {
  font-size: clamp(20px, 4vw, 4vw);
  margin: 0;
  color: #1c1c1c;
}

p {
  font-size: clamp(16px, 1.2vw, 1.2vw);
  font-family: "Source Sans Pro", sans-serif;
  line-height: 1.6;
  color: #797979;
}

.cover-image {
  margin-top: 2em;
  width: 100%;
  border-radius: 40px;
  cursor: pointer;
}

.type-meta {
  margin-left: 2em;
  border-radius: 30px;
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
  font-size: 1.4em;
  font-weight: 600;
  background-color: white;
  color: #1c1c1c;
  border-radius: 15px;
  border: 4px solid #1c1c1c;
  padding: 0.5em;
  bottom: 0;
  left: 50%;
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
  transition: opacity 0.2 ease-in-out;
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

@media (max-width: 700px) {
  .project-container {
    padding: 1em 1em 2em 1em;
    width: 90vw;
    border-radius: 15px;
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