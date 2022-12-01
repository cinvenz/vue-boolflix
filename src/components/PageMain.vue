<template>
  <div>
    <div>
      <h2 v-if="arrMovies.length > 0">Movies</h2>
      <div class="row row-cols-4 g-4 container-cards py-5">
        <CardTvSeries
          v-for="movie in arrMovies"
          :key="movie.id"
          :movie="movie"
          :name="movie.title"
          :originallanguage="movie.original_language"
          :originaltitle="movie.original_title"
          :vote="movie.vote_average"
        />
      </div>
    </div>
    <div>
      <h2 v-if="arrTv.length > 0" class="series">TV series</h2>
      <div class="row row-cols-4 g-4 container-cards py-5">
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
    </div>
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

<style lang="scss" scoped>
.serie {
  display: block;
}
</style>
