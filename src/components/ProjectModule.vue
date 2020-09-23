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
          <img class="preview-platform-icons" :src="require(`../assets/icons/${platform}.svg`)" :alt="`link for ${platform}`" />
        </a>
      </div>
    </header>
    <p>
      Mitio is a weather app that I created to have a better understanding of the web development process and what it takes to build a web app. I wanted to create a simple-looking weather app without using any third-party libraries (except for animation). I tried to keep the design simple and practical where user can have access to the weather information without much hassle. You can go here for live preview. It only works on desktop, not on mobile devices.
      To give a basic idea of the functionality of the website, I used the geolocation API to fetch the user’s location and then weatherbit API to receive necessary weather data. It was then processed into meaningful information and then rendered in the browser.
    </p>
    <img
      class="cover-image"
      src="../assets/images/projects/mitio_cover.png"
      :alt="`Screenshot of ${projectName}`"
    />
    <button @click="readMore" class="more">Read More...</button>
  </article>
</template>

<script>
export default {
  name: "ProjectModule",
  data() {
    return {
      title: "mitio",
      type: "Programming",
      preview: {
        github: "https://github.com/ayushman-git/weather-app",
        behance: "https://www.behance.net/search/projects/?search=portfolio",
        live: "https://weathertestapp.netlify.app"
      },
      read: "https://medium.com/@Duoro/mitio-weather-simplified-ae8bce8626db"
    };
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
</style>