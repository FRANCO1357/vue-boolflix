<template>
  <div>
    <BaseHeader @search-text="fatchData"/>
    <BaseMain :movies-array="movies" :series-array="series"/>
  </div>
</template>

<script>
import axios from 'axios'
import BaseHeader from './components/BaseHeader.vue';
import BaseMain from './components/BaseMain.vue';

export default {
  name: 'App',
  data(){
    return{
      searchText: '',
      apiKey: '4cb7ddb10a4d729a1e36c4727937b74a',
      movies: [],
      series: [],
    }
  },
  components: {
    BaseHeader,
    BaseMain
  },
  methods: {
    getMovies(){
      axios .get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.searchText}`).then((res) =>{
      console.log(res.data.results);
      this.movies = res.data.results;
    })    
    },
    getSeries(){
      axios .get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${this.searchText}`).then((res) =>{
      console.log(res.data.results);
      this.series = res.data.results;
    })    
    },
    fatchData(value){
      this.searchText = value;
      this.getMovies();
      this.getSeries();
    },
  }
}


</script>

<style lang="scss">

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: sans-serif;
}
img{
  max-width: 100%;
}

ul{
  background-color: green;
  display: flex;
  flex-direction: column;
  li{
    list-style-type: none;
    background-color: red;
  }
}

</style>
