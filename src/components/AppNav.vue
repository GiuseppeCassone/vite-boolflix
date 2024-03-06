<script>
import {store} from '../store.js';

    export default {
        name: 'AppNav',

        data() {

            return {
                store,
            }
        },
    }
</script>

<template>
    <nav class="navbar">
            <div class="container-fluid">
                <a class="navbar-brand text-danger fw-bold">Boolflix</a>
                <div class="d-flex" role="search">
                <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="store.searchText">
                <button @click="$emit('search')" class="btn btn-outline-success" type="submit">Search</button>
                </div>
            </div>
    </nav>
</template>

<style lang="scss">

    .navbar{
        background-color: #141414;
    }
</style>