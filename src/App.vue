<template>
  <div>
    <input type="text" v-model="searchText" @keyup.enter="getMovies">
    <ul>
      <li v-for="movie in movies" :key="movie.id">{{movie.title}} - {{movie.original_title}} - {{movie.original_language}} - {{movie.vote_average}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  data(){
    return{
      searchText: '',
      apiKey: '4cb7ddb10a4d729a1e36c4727937b74a',
      movies: [],
    }
  },
  components: {
    
  },
  methods: {
    getMovies(){
      axios .get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.searchText}`).then((res) =>{
      console.log(res.data.results);
      this.movies = res.data.results;
    })    
    }
  }
}


</script>

<style lang="scss">

</style>
