<script>

    export default {
        name: 'AppMovie',

        props: {
            movies: Object,
        },

        methods: {
            flagLanguage() {
                let switchedFlag = this.movies.original_language;
                switch(this.movies.original_language){

                    case "en":
                         switchedFlag = "us";
                         break;
                    case "ja":
                        switchedFlag = "jp";
                        break;
                    case "ko":
                        switchedFlag = "kr";
                        break;
                    case "zh":
                        switchedFlag = "cn";
                        break;
                    case "cs":
                        switchedFlag = "cz";
                        break;
                    case "hi":
                        switchedFlag = "in";
                        break;
                };
                return `https://flagcdn.com/16x12/${switchedFlag}.png`;
            },

            posterImg() {
                return `https://image.tmdb.org/t/p/w342/${this.movies.poster_path}.jpg`;
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

    <div class="card col-12 col-md-6 col-lg-3 gap-2">
        <div class="card-img"><img :src="posterImg()" alt=""></div>
        <div class="info-box">
            <h2 class="fs-5"><span>Titolo: </span>{{ movies.title }}</h2>
            <h3 class="fs-6"><span>Titolo originale: </span>{{ movies.original_title }}</h3>
            <div><span>Lingua: </span><img :src="flagLanguage()" alt=""></div>
            <div class="d-flex"><span>Voto: </span><i v-for="star in generateStars()" :class="star" class="text-warning ps-2"></i></div>
            <p><span>Trama: </span>{{ movies.overview }}</p>
        </div>
    </div>

</template>

<style lang="scss">

    .card{
        position: relative;
        // width: calc(100% / 4);
        height: 450px;
        border-radius: 0px;

        .card-img {
            width: 100%;
            height: 100%;

            img{
                width: 100%;
                height: 100%;
                object-fit: cover;
            }
        }
        

        .info-box{
            position: absolute;
            top: 0;
            left: 0;

            width: 100%;
            height: 100%;
            padding: 20px;
            display: none;

            background-color: rgba(0, 0, 0, 0.6);
            color: white;

            span{
                color: #FF0011;
            }

            p{
                font-size: 12px;
            }


        }

    }

    .card:hover{

        .info-box{
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
            gap: 8px;
        }
    }

</style>