<template>
    <div class="card col-12 col-md-4 col-lg-five">
        <div class="poster">
            <template v-if="card.poster_path">
                <img  :src="`https://image.tmdb.org/t/p/w500${card.poster_path}`" :alt="`${card.original_title || card.original_name}`">
            </template>
            <template v-else>
                <img src="https://webpersonalization.com.br/wp-content/plugins/download-manager/assets/images/img-404.png" alt="">
            </template> 
        
            <div class="inner-card">
                <h3>{{ card.title || card.name }}</h3>
                <!-- <h4>{{ card.original_title || card.original_name }}</h4> -->
                <div class="row subtitle">
                    <div class="col-10">
                        <div class="vote_average" v-for="(number, index) in 5" :key="index">
                            <i v-if="index <= Math.floor(card.vote_average / 2)" class="fas fa-star"></i>
                            <i v-else class="far fa-star"></i>
                        </div>
                    </div>
                    <div class="col-2 text-align-right" v-if="card.original_language">
                        <lang-flag :iso="card.original_language" :title="card.original_title || card.original_name"/>
                    </div>
                </div>
                <template v-if="card.overview">
                    <p>{{ card.overview }}</p>       
                </template>
            </div>

        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: "Card",
    components: {
        LangFlag
    },
    props: ['card']
}
</script>

<style lang="scss" scoped>
.card {
    & {
        transition: all 1s;
        padding: 10px;
        cursor: pointer;
    }
    
    .poster {
        position: relative;
        img {
            width: 100%;
            height: 350px;
            object-fit: cover;
            object-position: center;
        }
    }
    .inner-card {
        display: none;
        position: absolute;
        background-color: rgba(0, 0, 0, 0.8);
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        padding: 20px;
    }

    p {
        text-align: justify;
    }
    
    &:hover .inner-card {
        display: block;
        overflow: auto;
        border: 1px solid white;
    }

    .subtitle {
        margin: 10px 0px;
    }

    .vote_average {
        text-align: right;
        display: inline;
        i {
            color: yellow;
        }
    }

}
</style>