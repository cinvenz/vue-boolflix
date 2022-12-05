<template>
  <main>
    <div>
      <h2 v-if="arrMovies.length > 0" class="movies text-center text-uppercase text-danger pt-5">
        Movies
      </h2>
      <div class="row row-cols-4 g-4 container-cards py-5">
        <CardTvSeries
          v-for="movie in arrMovies"
          v-show="movie.poster_path"
          :key="movie.id"
          :movie="movie"
          :name="movie.title"
          :originallanguage="movie.original_language"
          :originaltitle="movie.original_title"
          :vote="InsertStar(movie.vote_average)"
        />
      </div>
    </div>
    <div>
      <h2 v-if="arrTv.length > 0" class="series text-center text-uppercase text-danger pt-4">
        TV series
      </h2>
      <div class="row row-cols-4 g-4 container-cards py-5">
        <CardTvSeries
          v-for="movie in arrTv"
          v-show="movie.poster_path"
          :key="movie.id"
          :movie="movie"
          :name="movie.name"
          :originallanguage="movie.original_language"
          :originaltitle="movie.original_name"
          :vote="InsertStar(movie.vote_average)"
        />
      </div>
    </div>
  </main>
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
  methods: {
    InsertStar(vote) {
      return Math.ceil(vote / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: rgb(78, 73, 73);
}
.movies {
  text-shadow: 4px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
}
.series {
  text-shadow: 4px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
}
</style>
