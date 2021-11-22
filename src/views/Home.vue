<template>
  <div class="home">
    "Stargazers GitHub Repo Project"
    <!-- <h1>{{ message }}</h1> -->
    <h1>Vuejs Repo</h1>
    <div v-for="info in repoData" v-bind:key="info.id">
      {{ info.forks_count }}
      {{ info.watchers }}
      {{ info.stargazers_count }}
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Hi!",
      repoData: [],
    };
  },
  created: function () {
    this.getRepo();
  },
  methods: {
    getRepo: function () {
      axios
        .get("https://api.github.com/repos/vuejs/vue")
        .then((response) => {
          this.repoData = [...this.repoData, response.data];
          console.log("All Vuejs Repo data", this.repoData);
        })
        .catch((error) => {
          console.log(error.response);
          this.repoData = {};
        });
    },
  },
};
</script>
