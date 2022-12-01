<template>
  <div class="row row-cols-5 g-4 container-cards py-5">
    <h2 v-if="arrMovies.length > 0">Movies</h2>
    <CardTvSeries
      v-for="movie in arrMovies"
      :key="movie.id"
      :movie="movie"
      :name="movie.title"
      :originallanguage="movie.original_language"
      :originaltitle="movie.original_title"
      :vote="movie.vote_average"
    />
    <h2 v-if="arrTv.length > 0">TV series</h2>
    <CardTvSeries
      v-for="movie in arrTv"
      :key="movie.id"
      :movie="movie"
      :name="movie.name"
      :originallanguage="movie.original_language"
      :originaltitle="movie.original_name"
      :vote="movie.vote_average"
    />
  </div>
</template>

<script>
import CardTvSeries from "@/components/CardTvSeries.vue";

export default {
  name: "PageMain",
  components: {
    CardTvSeries,
  },
  props: {
    arrMovies: Array,
    arrTv: Array,
  },
};
</script>

<style></style>
