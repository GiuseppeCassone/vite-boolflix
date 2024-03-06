<script>

    export default {
        name: 'AppMovie',

        props: {
            movies: Object,
        },

        methods: {
            flagLanguage(flag) {
                return `https://flagcdn.com/16x12/${flag}.png`;
            },

            posterImg() {
                return `https://image.tmdb.org/t/p/w300/${this.movies.poster_path}.jpg`;
            },

            generateStars() {
                const voteStars = Math.round(this.movies.vote_average / 2);
                const stars = [];

                for (let i = 0; i < voteStars; i++) {
                    stars.push('fa-solid fa-star');
                }

                for (let i = voteStars; i < 5; i++) {
                    stars.push('fa-regular fa-star');
                }

                return stars;
            },
        }
    }

</script>

<template>

    <div class="card gap-2 text-center">
        <div><img :src="posterImg()" alt=""></div>
        <h2>{{ movies.title }}</h2>
        <h3>{{ movies.original_title }}</h3>
        <div><img :src="flagLanguage(movies.original_language)" alt=""></div>
        <div class="d-flex justify-content-center"><i v-for="star in generateStars()" :class="star"></i></div>
    </div>

</template>

<style lang="scss">

    .card{
        width: calc(100% / 4);
        border-radius: 0px;

    }

</style>