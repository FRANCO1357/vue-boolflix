<template>
    <main>
        <div id="film-section">
            <h2 v-if="moviesArray.length > 0">Film</h2>
            <ul v-for="movie in moviesArray" :key="movie.id">
                <li>{{movie.title}}</li>
                <li>{{movie.original_title}}</li>
                <li v-if="movie.poster_path"><img :src="baseUrl + movie.poster_path" :alt="movie.title"></li>
                <li v-else><img :src="cover"></li>
                <li>
                    <div v-if="movie.original_language === 'it' || movie.original_language === 'en'">
                        <img :src="getMoviesLang(movie)" alt="">
                    </div>
                    <div v-else>
                        {{movie.original_language}}
                    </div>
                </li>
                <li><i v-for="n in 5" :key="n" class="fa-star" :class="fiveStarVote(movie.vote_average, n)"></i></li>
            </ul>
        </div>
        <div id="series-section">
            <h2 v-if="seriesArray.length > 0">Serie</h2>
            <ul v-for="serie in seriesArray" :key="serie.id">
                <li>{{serie.name}}</li>
                <li>{{serie.original_name}}</li>
                <li v-if="serie.poster_path"><img :src="baseUrl + serie.poster_path" :alt="serie.name"></li>
                <li v-else><img :src="cover"></li>
                <li>
                    <div v-if="serie.original_language === 'it' || serie.original_language === 'en'">
                        <img :src="getMoviesLang(serie)" alt="">
                    </div>
                    <div v-else>
                        {{serie.original_language}}
                    </div>
                </li>
                <li><i v-for="n in 5" :key="n" class="fa-star" :class="fiveStarVote(serie.vote_average, n)"></i></li>
            </ul>
        </div>
    </main>
</template>

<script>
export default{
    name: 'BaseMain',
    data(){
        return{
            baseUrl: 'https://image.tmdb.org/t/p/w342',
            cover: "https://previews.123rf.com/images/pxlprostudio/pxlprostudio1907/pxlprostudio190701502/127513726-icona-relativa-alla-striscia-di-pellicola-sullo-sfondo-per-la-progettazione-grafica-e-web-illustrazi.jpg?fj=1",
        }
    },
    props:{
        moviesArray: Array,
        seriesArray: Array,
    },
    methods:{
        fiveStarVote(vote, n) {
            if (vote > 1){
                vote = Math.ceil(vote / 2);
                if(vote >= n){
                    return 'fa-solid'
                } else{
                    return 'fa-regular'
                }
            } else{
                return 'fa-regular';
            }
        },
        getMoviesLang(movie){
            return require(`../assets/flags/${movie.original_language}.png`)
        },
        getSeriesLang(serie){
            return require(`../assets/flags/${serie.original_language}.png`)
        }
    },
}
</script>

<style lang="scss" scoped>
</style>