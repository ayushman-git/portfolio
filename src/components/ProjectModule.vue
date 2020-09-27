<template>
  <article class="project-container">
    <header>
      <div class="title-type">
        <h1>{{ projectName }}</h1>
        <div class="type-meta">{{ type }}</div>
      </div>
      <div>
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
    />

    <button @click="readMore" class="more">
      <span v-if="type === 'Graphic Design'">
        Watch
        <svg
          xmlns="http://www.w3.org/2000/svg"
          height="24"
          viewBox="0 0 24 24"
          width="24"
        >
          <path d="M0 0h24v24H0z" fill="none" />
          <path d="M8 5v14l11-7z" /></svg
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
      required: true
    },
    content: {
      content: {
        type: String,
        required: false
      }
    },
    preview: {
      type: Object,
      required: true
    },
    coverImage: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: true
    },
    read: {
      type: String,
      required: true
    }
  },

  computed: {
    projectName() {
      let projectName = this.title;
      projectName = projectName.charAt(0).toUpperCase() + projectName.slice(1);
      projectName = projectName.replace(/_/g, " ");
      return projectName;
    }
  },
  methods: {
    readMore() {
      window.open(this.read, "_blank", "noopener");
    }
  }
};
</script>

<style scoped>
.project-container {
  position: relative;
  display: flex;
  flex-flow: column nowrap;
  padding: 2em 2em 4em 2em;
  width: 80vw;
  background-color: white;
  border-radius: 40px;
  color: #1c1c1c;
}

header {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: space-between;
}

.title-type {
  display: flex;
  align-items: center;
  flex-flow: row nowrap;
}

h1 {
  margin: 0;
  color: #1c1c1c;
}

p {
  font-family: "Source Sans Pro", sans-serif;
  line-height: 1.6;
  color: #757575;
}

.cover-image {
  margin-top: 2em;
  width: 100%;
  border-radius: 40px;
}

.type-meta {
  margin-left: 2em;
  border-radius: 30px;
  background-color: #e8e8e8;
  padding: 0.5em 1.5em;
  color: #939393;
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
</style>