<template>
  <div class="container my-5">
    <h1 class="text-center mb-4">My Projects</h1>

    <div class="row d-flex justify-content-center">
      <div class="col-md-4 mb-3" v-for="project in projects" :key="project.id">
        <div class="card shadow">
          <img :src="project.thumbnail" class="card-img-top" alt="" />
          <div class="card-body">
            <h5 class="card-title">{{ project.name }}</h5>
            <p class="card-text">
              {{ project.description }}
            </p>
            <!-- <a href="#" class="btn btn-primary">Go somewhere</a> -->
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