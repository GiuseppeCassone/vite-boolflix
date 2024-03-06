<script>

    export default {
        name: 'AppMovie',

        props: {
            movies: Object,
        },
    }

</script>

<template>

    <div class="card">
        <h2>{{ movies.title }}</h2>
        <h3>{{ movies.original_title }}</h3>
        <span>{{ movies.original_language }}</span>
        <span>{{ movies.vote_average }}</span>
    </div>

</template>

<style lang="scss">

</style>