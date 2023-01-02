<template>
  <div class="container my-5">
    <div class="row d-flex justify-content-between">
      <div class="col-md-7">
        <h1 class="mb-4">I am {{ this.profile.name }}</h1>
        <p v-html="this.profile.about"></p>
      </div>

      <div class="col-md-4">
        <div class="image">
          <img :src="this.profile.image" alt="" class="img-fluid rounded" />
        </div>

        <div class="social mt-3">
          <ul class="list-group" v-for="contact in contacts" :key="contact.id">
            <li class="list-group-item">
              <a @click="redirect(contact.link)">{{ contact.name }}</a>
            </li>
          </ul>
        </div>
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
