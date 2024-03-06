<script>

    export default {
        name: 'AppMovie',

        props: {
            movies: Object,
        },

        methods: {
            flagLanguage(flag) {
                return `https://flagcdn.com/16x12/${flag}.png`;
            }
        }
    }

</script>

<template>

    <div class="card gap-2 text-center">
        <h2>{{ movies.title }}</h2>
        <h3>{{ movies.original_title }}</h3>
        <div><img :src="flagLanguage(movies.original_language)" alt=""></div>
        <span>{{ movies.vote_average }}</span>
    </div>

</template>

<style lang="scss">

    .card{
        width: calc(100% / 4);
        border-radius: 0px;

    }

</style>