<template>
  <div class="container my-5">
    <div class="row d-flex justify-content-between">
      <div class="col-md-7">
        <h1 class="mb-4">I am {{ this.profile.name }}</h1>
        <p v-html="this.profile.about"></p>
      </div>

      <div class="col-md-4">
        <div class="image float-right">
          <img :src="this.profile.image" alt="" class="img-fluid rounded" />
        </div>
      </div>
    </div>

    <div class="row">
      <div
        class="social text-center col-md-1 mt-3"
        v-for="contact in contacts"
        :key="contact.id"
      >
        <a @click="redirect(contact.link)">{{ contact.name }}</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HomeView",
  data() {
    return {
      profile: [],
      contacts: [],
    };
  },
  methods: {
    async getProfile() {
      let { data } = await axios.get("/profile");

      this.profile = data.data;
    },

    async getContact() {
      let { data } = await axios.get("/contacts");

      this.contacts = data.data;
    },

    redirect(url) {
      window.location.href = "https://" + url;
    },
  },

  mounted() {
    this.getProfile();
    this.getContact();
  },
};
</script>

<style>
p {
  color: #18181b;
}

h1 {
  font-size: 48px;
  font-weight: bold;
  background: -webkit-linear-gradient(#00c6ff, #0072ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

img {
  height: 250px !important;
}

.social ul li {
  border: none;
  cursor: pointer;
  background: none;
}
</style>
