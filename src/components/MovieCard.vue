<template>
  <div class="card" v-on:click="goToDetailsPage(movie.id)">
    <div class="card-body">
      <div :style="{'background-image': `url(${movie.poster})`}" class="card-cover-img"/>
      <p class="card-title warp" >{{ movie.name }}</p>
      <p class="card-text">{{ movie.description }}</p>
      <div class="d-flex">
        <div :class="`badge-item ${(movie.rating < 4 && movie.rating > 0 && 'badge-red') || (movie.rating < 7 && movie.rating > 4 && 'badge-purple') || (movie.rating < 10 && movie.rating > 7 && 'badge-success')}`">
          <img src="../assets/icons/score.png" class="badge-icon" />
          <span class="badge-text">{{ movie.rating }}</span>
        </div>

        <div class="badge-item badge-blue">
          <img src="../assets/icons/genre.png" class="badge-icon" />
          <span class="badge-text">{{ movie.genre }}</span>
        </div>

        <div class="badge-item badge-purple">
          <img src="../assets/icons/duration.png" class="badge-icon" />
          <span class="badge-text">{{ movie.duration }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "movie-card",
  props: {
    movie: Object,
  },
  methods: {
    goToDetailsPage: function(id) {
      this.$router.push("/movie/" + id);
    },
  },
};
</script>

<style scoped>
@import "../assets/styles/common.css";
</style>
