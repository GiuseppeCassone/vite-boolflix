<script>

    export default {
        name: 'AppMovie',

        props: {
            movies: Object,
        },
    }

</script>

<template>

    <div class="card gap-2">
        <h2>{{ movies.title }}</h2>
        <h3>{{ movies.original_title }}</h3>
        <span>{{ movies.original_language }}</span>
        <span>{{ movies.vote_average }}</span>
    </div>

</template>

<style lang="scss">

    .card{
        width: calc(100% / 4);
        border-radius: 0px;

    }

</style>