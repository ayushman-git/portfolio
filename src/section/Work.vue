<template>
  <div class="work-container">
    <h1>Work</h1>
    <ul class="criteria-list">
      <li v-for="item in criteria" :key="item">
        <FilterTags
          v-on:clicked="criteriaSeletion"
          :type="item"
          :state="selectedType === item"
        />
      </li>
    </ul>
    <div
      class="project-holder"
      v-for="project in filterProject"
      :key="project.index"
    >
      <ProjectModule
        v-on:emitImage="imagePreview"
        :title="Object.keys(project).toString()"
        :preview="project[Object.keys(project).toString()].preview_links"
        :type="project[Object.keys(project).toString()].category"
        :read="project[Object.keys(project).toString()].article"
        :coverImage="project[Object.keys(project).toString()].image"
        :content="project[Object.keys(project).toString()].content"
        class="module"
      />
    </div>
  </div>
</template>

<script>
import { TimelineLite } from "gsap/dist/gsap";

import ProjectModule from "../components/ProjectModule";
import FilterTags from "../components/FilterTags";

import project from "../assets/projectData";
export default {
  name: "Work",
  components: {
    ProjectModule,
    FilterTags,
  },
  data() {
    return {
      selectedType: "Favorites",
      criteria: ["Favorites", "Programming", "Graphic Design"],
    };
  },
  methods: {
    criteriaSeletion(type) {
      this.selectedType = type;
    },
    imagePreview(e) {
      this.$emit('emitImage', e)
    }
  },
  computed: {
    filterProject() {
      return project.filter((pr) => {
        if (this.selectedType === "Favorites") {
          return pr[Object.keys(pr).toString()].favorite === this.selectedType;
        }
        return pr[Object.keys(pr).toString()].category === this.selectedType;
      });
    },
  },
  watch: {
    selectedType: function () {
      const project = document.querySelector(".project-holder").firstChild;
      const tl = new TimelineLite();

      tl.from(project, {
        y: 200,
        duration: 0.4,
        opacity: 0,
      });
    },
  },
};
</script>
<style scoped>
.work-container {
  display: flex;
  flex-flow: column;
  align-items: center;
  background: url("../assets/pattern/graph-paper.svg");
}

.module {
  margin-bottom: 10em;
  transition: box-shadow 0.4s ease-in-out;
}

.module:hover {
  box-shadow: 0 0 10px 10px rgba(0, 0, 0, 0.2);
}

.criteria-list {
  padding: 0;
  display: flex;
  flex-flow: row wrap;
  justify-content: flex-start;
  width: 70vw;
  max-width: 1000px;
  list-style-type: none;
}

.criteria-list li {
  margin-right: 1em;
}

.project-holder {
  margin-top: 2em;
}

@media (max-width: 700px) {
  .criteria-list {
    width: 90vw;
  }
  .criteria-list li {
    margin-bottom: 1em;
    font-size: 14px;
  }
}
</style>