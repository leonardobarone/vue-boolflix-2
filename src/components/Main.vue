<template>
    <main>
        <section id="films" class="container-fluid">
            <h2>Film</h2>
            <div v-if="!messageFilm" class="row">
                <Card v-for="film in films" :key="film.id" :card="film" />
            </div>
            <div v-else>
                <h3 class="message">La ricerca "{{query}}" non ha prodotto risultati.</h3>
            </div>
        </section>
        <section id="series" class="container-fluid">
            <h2>Serie TV</h2>
            <div v-if="!messageSerie" class="row">
                <Card v-for="serie in series" :key="serie.id" :card="serie" />
            </div>
            <div v-else>
                <h3 class="message">La ricerca "{{query}}" non ha prodotto risultati.</h3>
            </div>
        </section>
    </main>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue';

export default {
    name: "Main",
    components: {
        Card
    },
    data() {
        return {
            // Credentials
            params: {
                 api_key: "933f816273dcac2d9bb3de85d7f0a2c6",
                 language: "it-IT",
            },
           films: [],
           series: [],
           messageFilm: false,
           messageSerie: false 
        }
    },
    props: ['query'],
    created() {
            // Request Films Start
            axios.get(' https://api.themoviedb.org/3/movie/popular', {
                params: this.params
            })
            .then((response) => {
                this.films = response.data.results;             
            })
            // Request Series Start
            axios.get(' https://api.themoviedb.org/3/tv/popular', {
                params: this.params
            })
            .then((response) => {
                this.series = response.data.results;             
            })
    },
    watch: {
        query: function() {
            // Query
            this.params.query = this.query;
            // Trash
            if (!this.query) {
                window.location.reload();
            }
            // Request Films
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: this.params
            })
            .then((response) => {
                this.films = response.data.results;
                // Message
                if (this.films.length == 0) {
                    this.messageFilm = true;
                } 
            })
            // Request Series
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: this.params
            })
            .then((response) => {
                this.series = response.data.results;
                // // Message
                if (this.series.length == 0) {
                    this.messageSerie = true;
                } 
            })
        }  
    }
}
</script>

<style lang="scss" scoped>

main {
    padding-top: 75px;
}

#films, #series, h2 {
    padding: 10px;
}

h2 {
    background-color: var(--grigio);
}

.message {
    padding-top: 10px;
}
</style>