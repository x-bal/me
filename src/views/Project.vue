<template>
  <div class="container my-5">
    <h1 class="text-center mb-4">My Projects</h1>

    <div class="row d-flex justify-content-center">
      <div class="col-md-4 mb-3" v-for="project in projects" :key="project.id">
        <div class="card shadow">
          <img :src="project.thumbnail" class="card-img-top" alt="" />
          <div class="card-body">
            <h5 :class="[textClass]">{{ project.name }}</h5>
            <p :class="[textClass]">
              {{ project.description }}
            </p>
            <button
              v-for="tag in project.tags"
              :key="tag.id"
              type="button"
              class="btn btn-sm btn-primary mr-1"
            >
              {{ tag.name }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Project",

  data() {
    return {
      projects: [],
      textClass: "text-dark",
    };
  },

  methods: {
    async getProjects() {
      let { data } = await axios.get("/projects");

      this.projects = data.data;
    },
  },

  mounted() {
    this.getProjects();
  },
};
</script>

<style scoped>
h1 {
  font-size: 48px;
  font-weight: bold;
}

.card {
  min-height: 22rem;
}

.card-img-top {
  height: 200px !important;
}
</style>