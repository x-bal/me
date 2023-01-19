<template>
  <div id="app" class="bg-me pb-5">
    <navbar />
    <router-view />
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";

export default {
  components: {
    Navbar: Navbar,
  },
};
</script>

<style>
html,
body {
  padding: 0;
  margin: 0;
}
/* Define styles for the default root window element */
:root {
  --background-color-primary: #fff;
  --background-color-navbar: #f4f4f5;
  --background-color-secondary: #fafafa;
  --accent-color: #cacaca;
  --text-primary-color: #222;
  --element-size: 4rem;
}

/* Define styles for the root window with dark - mode preference */
:root.dark-theme {
  --background-color-primary: #131313;
  --background-color-navbar: #18181b;
  --background-color-secondary: #2d2d30;
  --accent-color: #3f3f3f;
  --text-primary-color: #fff;
}

.bg-me {
  min-height: 100vh;
  background-color: var(--background-color-primary);
}

.navbar {
  background-color: var(--background-color-navbar);
}

* {
  color: var(--text-primary-color) !important;
}
</style>
