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
        <div class="author">
          {{ originaltitle }}
        </div>
        <div class="anno">
          {{ originallanguage }}
        </div>
        <div>
          {{ vote }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardTvSeries",
  props: {
    movie: Object,
    name: String,
    originallanguage: String,
    originaltitle: String,
    languageList: Array,
    vote: Number,
  },
};
</script>

<style></style>
