<script>

    export default {
        name: 'AppSeries',

        props: {
            series: Object,
        },

        methods: {
            flagLanguage(flag) {
                return `https://flagcdn.com/16x12/${flag}.png`;
            },

            posterImg() {
                return `https://image.tmdb.org/t/p/w300/${this.series.poster_path}.jpg`;
            },

            generateStars() {
                const voteStars = Math.round(this.series.vote_average / 2);
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

    <div class="card col-12 col-md-6 col-lg-3 gap-2 text-center">
        <div class="card-img"><img :src="posterImg()" alt=""></div>
        <div class="info-box">
            <h2 class="fs-5">{{ series.name }}</h2>
            <h3 class="fs-6">{{ series.original_name }}</h3>
            <div><img :src="flagLanguage(series.original_language)" alt=""></div>
            <div class="d-flex justify-content-center"><i v-for="star in generateStars()" :class="star" class="text-warning ps-2"></i></div>
            <p>Trama: {{ series.overview }}</p>
        </div>
    </div>

</template>

<style lang="scss">

    // .card{
    //     width: calc(100% / 4);
    //     height: 450px;
    //     border-radius: 0px;

    //     .card-img {
    //         width: 100%;
    //         height: 100%;

    //         img{
    //             width: 100%;
    //             height: 100%;
    //             object-fit: cover;
    //         }
    //     }
        

    //     .info-box{
    //         position: absolute;
    //         top: 0;
    //         left: 0;

    //         width: 100%;
    //         height: 100%;
    //         padding: 20px;
    //         display: none;

    //         background-color: rgba(0, 0, 0, 0.6);
    //         color: white;

    //         p{
    //             font-size: 12px;
    //         }
    //     }

    // }

</style>