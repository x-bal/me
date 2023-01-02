<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <img :src="this.brand" alt="Muhammad Iqbal" class="rounded-circle"
      /></router-link>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavAltMarkup"
        aria-controls="navbarNavAltMarkup"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav me-auto">
          <router-link class="nav-link" to="/about">About</router-link>
          <router-link class="nav-link" to="/projects">Projects</router-link>
          <router-link class="nav-link" to="/skills">Skills</router-link>
        </div>

        <div class="d-flex" role="search">
          <theme-button />
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import axios from "axios";
import ThemeButton from "./ThemeButton.vue";

export default {
  components: {
    ThemeButton: ThemeButton,
  },

  name: "Navbar",

  data() {
    return {
      brand: "",
    };
  },

  methods: {
    async getBrand() {
      let { data } = await axios.get("/profile");

      this.brand = data.data.image;
    },
  },

  mounted() {
    this.getBrand();
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@500&display=swap");
* {
  font-family: "JetBrains Mono", monospace;
}

nav {
  height: 150px;
  background-color: #f4f4f5;
}

.navbar-brand img {
  width: 40px;
  height: 40px !important;
}

.navbar-nav {
  margin-left: 34%;
}
.nav-link {
  color: v-bind(color) !important;
}
</style>