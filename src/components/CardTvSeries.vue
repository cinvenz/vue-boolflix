<template>
  <div>
    <div class="col">
      <div class="contents container-card">
        <div class="container-img">
          <img
            :src="`https://www.themoviedb.org/t/p/original${movie.poster_path}`"
            :alt="name"
            class="img-fluid"
          />
        </div>

        <div class="retro-movie">
          <h2 class="name fw-bold text-uppercase pt-3">
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
          <div>
            {{ overview }}
          </div>
        </div>
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
    overview: String,
  },
};
</script>

<style lang="scss" scoped>
img {
  width: 264px;
  height: 396px;
  object-fit: cover;
}

.retro-movie {
  overflow-y: scroll;
  width: 264px;
  height: 396px;
  font-size: 0.8rem;
  position: absolute;
  top: 0%;
  padding: 1rem;
  color: white;
  z-index: -2;
}

.cards:hover .retro-movie {
  background-color: black;
  transition: background-color 0.6s;
  z-index: 10;
}
</style>
