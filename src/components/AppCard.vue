<script>

    export default {
        name: 'AppCard',

        props: {
            infos: Object,
            cast: Array,
            genres: Object,
        },

        methods: {
            flagLanguage() {
                let switchedFlag = this.infos.original_language;
                switch(this.infos.original_language){

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
                return `https://image.tmdb.org/t/p/w342/${this.infos.poster_path}.jpg`;
            },

            generateStars() {
                const voteStars = Math.round(this.infos.vote_average / 2);
                const stars = [];

                for (let i = 0; i < voteStars; i++) {
                    stars.push('fa-solid fa-star');
                }

                for (let i = voteStars; i < 5; i++) {
                    stars.push('fa-regular fa-star');
                }

                return stars;
            },

            getCastNames() {
                if (this.cast && this.cast.length) {
                    let castNames = '';
                    const maxMemberCast = 5;
                    for (let i = 0; i < Math.min(this.cast.length, maxMemberCast); i++) {
                    castNames += this.cast[i].name;
                    if (i < Math.min(this.cast.length, maxMemberCast) - 1) {
                        castNames += ', ';
                    }
                    }
                    return castNames;
                } else {
                    return '';
                }
            },

            getGenresName() {
                if (this.infos.genre_ids && this.genres.length > 0) {
                        const genreNames = this.infos.genre_ids.map(genreId => {
                            const genre = this.genres.find(genre => genre.id === genreId);
                            return genre ? genre.name : '';
                        });
                        return genreNames.join(', ');
                    } else {
                        return '';
                    }
            }

        }
}

</script>

<template>

    <div class="card col-12 col-md-6 col-lg-3 gap-2">
        <div class="card-img"><img :src="posterImg()" alt=""></div>
        <div class="info-box">
            <h2 class="fs-5"><span>Titolo: </span>{{ infos.title ? infos.title : infos.name }}</h2>
            <h3 class="fs-6"><span>Titolo originale: </span>{{ infos.original_title ? infos.original_title : infos.original_name }}</h3>
            <div><span>Lingua: </span><img :src="flagLanguage()" alt=""></div>
            <div class="d-flex"><span>Voto: </span><i v-for="star in generateStars()" :class="star" class="text-warning ps-2"></i></div>
            <p v-if="infos.overview.length > 0"><span>Trama: </span>{{ infos.overview }}</p>
            <p v-if="cast && cast.length"><span>Cast: </span>{{ getCastNames() }}</p>
            <p v-if="getGenresName()"><span>Generi: </span>{{ getGenresName() }}</p>
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
            overflow-y: auto;
        }
    }

</style>