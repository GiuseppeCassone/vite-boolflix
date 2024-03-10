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
    <nav class="navbar navbar-expand-lg">
            <div class="container-fluid">
                <a class="navbar-brand fw-bold"><img src="/img/logo.boolflix.png" alt=""></a>
                <button class="navbar-toggler bg-light" type="button" data-bs-toggle="collapse" data-bs-target="#navbarTogglerDemo02" aria-controls="navbarTogglerDemo02" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse justify-content-between" id="navbarTogglerDemo02">
                    <ul class="navbar-nav">
                        <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="#">Home</a>
                        </li>
                        <li class="nav-item">
                        <a class="nav-link" href="#">Film</a>
                        </li>
                        <li class="nav-item">
                        <a class="nav-link" href="#">Serie TV</a>
                        </li>
                        <li class="nav-item">
                        <a class="nav-link" href="#">Original</a>
                        </li>
                        <li class="nav-item">
                        <a class="nav-link" href="#">Aggiunti di recente</a>
                        </li>
                        <li class="nav-item">
                        <a class="nav-link" href="#">La mia lista</a>
                        </li>
                    </ul>
                    <div class="d-flex" role="search">
                    <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="store.searchText">
                    <button @click="$emit('search')" class="btn btn-outline-success" type="submit">Search</button>
                    </div>
                </div>
            </div>
    </nav>
</template>

<style lang="scss">

    .navbar{
        background-color: #141414;

        .navbar-brand{
            width: 100px;
            color: #FF0011;

            img{
                width: 100%;
            }
            
            
            
        }

        .nav-link{
            color: rgb(174, 174, 174);

            &.active{
                color: white;
            }
        }
    }
</style>
