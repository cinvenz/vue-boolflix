<template>
  <div class="d-flex align-items-center justify-content-between px-5 container-header">
    <h1 class="fs-4 text-danger">BOOLFLIX</h1>
    <form @submit.prevent="$emit('queryChange', quaryString)">
      <label for="quary">
        <input
          id="quary"
          v-model="quaryString"
          type="text"
          name="quary"
          placeholder="Search movies or series..."
        />
      </label>
      <button>Cerca</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "PageHeader",
  data() {
    return {
      quaryString: "",
    };
  },
  methods: {
    SearchMovie(select) {
      this.$emit("queryChange", select);
      this.select = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.container-header {
  background-color: black;
  height: 4rem;
}
h1 {
  cursor: pointer;
}
</style>
