<template>
  <div>
    <PageHeader @queryChange="search" />
    <PageMain :arr-movies="arrMovies" :arr-tv="arrTv" />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader.vue";
import PageMain from "@/components/PageMain.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    PageHeader,
    PageMain,
  },
  data() {
    return {
      baseApiUrl: "https://api.themoviedb.org/3",
      apiKey: "1b92b636342bd4df839f77a1536d49f9",
      resultsLanguage: "it-IT",
      arrMovies: [],
      arrTv: [],
    };
  },
  methods: {
    search(value) {
      axios
        .get(`${this.baseApiUrl}/search/movie`, {
          params: {
            api_key: this.apiKey,
            query: value,
            language: this.resultsLanguage,
          },
        })
        .then((responseAxios) => {
          this.arrMovies = responseAxios.data.results;
          console.log(this.arrMovies);
        });
      axios
        .get(`${this.baseApiUrl}/search/tv`, {
          params: {
            api_key: this.apiKey,
            query: value,
            language: this.resultsLanguage,
          },
        })
        .then((responseAxios) => {
          this.arrTv = responseAxios.data.results;
          console.log(this.arrTv);
        });
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
@import url("https://fonts.googleapis.com/css2?family=Lato&display=swap");
body {
  font-family: "Lato", sans-serif;
  font-size: 0.8rem;
  background-color: rgb(78, 73, 73);
}
</style>
