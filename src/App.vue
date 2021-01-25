<template>
  <div id="app">
    
    <AddMovie @add-review="updateReview"/>
    <MovieCard v-for="(movie, i) in movies" 
      v-bind:key="i" 
      v-bind:review="movie"/>

    <router-view/>
  </div>
</template>

<script>
  import AddMovie from "./components/AddMovie";
  import MovieCard from "./components/MovieCard";

  export default {
    data(){
      return {
        movies: []
      }
    },

    components: {
      AddMovie,
      MovieCard
    },

    methods: {
      updateReview(movies){
        this.movies.push(movies);
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
  * {
    box-sizing: border-box;
    font-family: "Roboto";
  }

  body {
  background:rgb(143, 216, 197);
  color: black;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>