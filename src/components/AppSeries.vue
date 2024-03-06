<script>

    export default {
        name: 'AppSeries',

        props: {
            series: Object,
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
        <h2>{{ series.name }}</h2>
        <h3>{{ series.original_name }}</h3>
        <div><img :src="flagLanguage(series.original_language)" alt=""></div>
        <span>{{ series.vote_average }}</span>
    </div>

</template>

<style lang="scss">

    .card{
        width: calc(100% / 4);
        border-radius: 0px;

    }

</style>