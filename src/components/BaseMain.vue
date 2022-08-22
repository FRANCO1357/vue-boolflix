<template>
    <main>
        <div id="film-section">
            <h2 v-if="moviesArray.length > 0">Film</h2>
            <ul v-for="movie in moviesArray" :key="movie.id">
                <li>{{movie.title}}</li>
                <li>{{movie.original_title}}</li>
                <li><img :src="baseUrl + movie.poster_path" :alt="movie.title"></li>
                <li><img :src="cover"></li>
                <li>
                    <div v-if="movie.original_language === 'it' || movie.original_language === 'en'">
                        <img :src="require(`../assets/flags/${movie.original_language}.png`)" alt="">
                    </div>
                    <div v-else>
                        {{movie.original_language}}
                    </div>
                </li>
                <li>{{fiveStarVote(movie.vote_average)}}</li>
            </ul>
        </div>
        <div id="series-section">
            <h2 v-if="seriesArray.length > 0">Serie</h2>
            <ul v-for="serie in seriesArray" :key="serie.id">
                <li>{{serie.name}}</li>
                <li>{{serie.original_name}}</li>
                <li><img :src="baseUrl + serie.poster_path" :alt="serie.name"></li>
                <li>
                    <div v-if="serie.original_language === 'it' || serie.original_language === 'en'">
                        <img :src="require(`../assets/flags/${serie.original_language}.png`)" alt="">
                    </div>
                    <div v-else>
                        {{serie.original_language}}
                    </div>
                </li>
                <li>{{fiveStarVote(serie.vote_average)}}</li>
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
        }
    },
    props:{
        moviesArray: Array,
        seriesArray: Array,
    },
    methods:{
        fiveStarVote(vote) {
            if (vote > 1){
                return Math.ceil(vote / 2);
            } else{
                return '';
            }
        },
    },
    computed:{
        cover(){
            if(!this.movie.poster_path) return "https://www.altavod.com/content/rad";
            return this.baseUlr + this.movie.poster_path
        }
    }
}
</script>

<style lang="scss" scoped>
</style>