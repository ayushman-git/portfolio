<template>
  <div class="work-container">
    <h1>Work</h1>
    <ul class="criteria-list">
      <li v-for="item in criteria" :key="item">
        <FilterTags v-on:clicked="criteriaSeletion" :type="item" />
      </li>
    </ul>
    <ProjectModule class="module" />
  </div>
</template>

<script>
import ProjectModule from "../components/ProjectModule";
import FilterTags from "../components/FilterTags";
export default {
  name: "Work",
  components: {
    ProjectModule,
    FilterTags
  },
  data() {
    return {
      selectedType: "",
      criteria: ["Favorites", "Programming", "UI Design", "Graphic Design"]
    };
  },
  methods: {
    criteriaSeletion(type) {
      this.selectedType = type;
    }
  }
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
}

.criteria-list {
  display: flex;
  justify-content: space-between;
  list-style-type: none;
  align-self: flex-start;
}
</style>