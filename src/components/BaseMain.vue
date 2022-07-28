<template>
    <div>
        <ul>
            <li v-for="movie in moviesArray" :key="movie.id">
            {{movie.title}} - 
            {{movie.original_title}} - 
            <img :src="baseUrl + movie.poster_path" :alt="movie.title">
            <div v-if="movie.original_language === 'it' || movie.original_language === 'en'">
                <img :src="require(`../assets/flags/${movie.original_language}.png`)" alt="">
            </div>
            <div v-else>
                {{movie.original_language}}
            </div>
            {{movie.vote_average}}
            </li>
        </ul>
        <ul>
            <li v-for="serie in seriesArray" :key="serie.id">
            {{serie.name}} - 
            {{serie.original_name}} - 
            <img :src="baseUrl + serie.poster_path" :alt="serie.name">
            <div v-if="serie.original_language === 'it' || serie.original_language === 'en'">
                <img :src="require(`../assets/flags/${serie.original_language}.png`)" alt="">
            </div>
            <div v-else>
                {{serie.original_language}}
            </div>
            {{serie.vote_average}}
            </li>
        </ul>
    </div>
</template>

<script>
export default{
    name: 'BaseMain',
    data(){
        return{
            baseUrl: 'https://image.tmdb.org/t/p/w342',
        }
    },
    props:{
        moviesArray: Array,
        seriesArray: Array,
    }
}
</script>

<style lang="scss" scoped>
</style>