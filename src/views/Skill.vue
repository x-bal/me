<template>
  <div class="container my-5">
    <h1 class="text-center mb-4">My Skills</h1>

    <div class="row d-flex justify-content-center">
      <div
        class="col-md-3 mb-3 text-center"
        v-for="skill in skills"
        :key="skill.id"
      >
        <div class="card">
          <div class="card-body">
            <img :src="skill.logo" class="img-fluid" alt="" />
            <h5 class="card-title">{{ skill.name }}</h5>
            <p class="card-text">{{ skill.experience }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Skill",

  data() {
    return {
      skills: [],
    };
  },

  methods: {
    async getSkills() {
      let { data } = await axios.get("/skills");

      this.skills = data.data;
    },
  },

  mounted() {
    this.getSkills();
  },
};
</script>

<style scoped>
h1 {
  font-size: 48px;
  font-weight: bold;
}

img {
  height: 120px !important;
}

.card {
  border: none;
}
</style>