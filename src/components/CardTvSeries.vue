<template>
  <div>
    <div class="col">
      <div class="contents text-center container-card p-3">
        <img
          :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`"
          :alt="name"
          class="img-fluid"
        />
        <h2 class="name fw-bold text-uppercase pt-3 pb-2">
          {{ name }}
        </h2>
        <div>
          {{ originaltitle }}
        </div>
        <div>
          <lang-flag :iso="movie.original_language" />
        </div>

        <font-awesome-icon
          v-for="i in vote.vote"
          :key="i"
          class="text-warning"
          icon="fa-solid fa-star"
        />
        <font-awesome-icon
          v-for="i in vote.maxVote - vote.vote"
          :key="i"
          class="text-warning"
          icon="fa-regular fa-star"
        />
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";

export default {
  name: "CardTvSeries",
  components: {
    LangFlag,
  },
  props: {
    movie: Object,
    name: String,
    originallanguage: String,
    originaltitle: String,
    languageList: Array,
    vote: Object,
  },
};
</script>

<style></style>
