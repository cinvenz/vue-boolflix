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
          :overview="movie.overview"
          class="cards"
        />
      </div>
    </div>
    <div>
      <h2 v-if="arrTv.length > 0" class="series text-center text-uppercase text-danger pt-2">
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
          :overview="movie.overview"
          class="cards"
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
      const maxVote = 5;
      const trueMaxVote = 10;

      return {
        vote: Math.ceil((vote * maxVote) / trueMaxVote),
        maxVote,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
.cards {
  margin-top: 0;
  margin-bottom: 6rem;
  position: relative;
  width: 18rem;
  height: 28rem;
  margin: auto;
}
.movies {
  text-shadow: 4px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
}
.series {
  text-shadow: 4px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
}
</style>
