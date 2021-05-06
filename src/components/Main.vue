<template>
    <main class="flex f-wrap justify-center">
        <div v-for="(album, index) in albums" :key="index" 
        class="card-wrapper"
        >
            <Card :infos="album" />
        </div>
    </main>
</template>

<script>
import Card from './Card';
import axios from 'axios';

export default {
    name: 'Main',
    components: {
        Card,
    },
     data() {
        return {
            apiURL: 'https://flynn.boolean.careers/exercises/api/array/music',
            albums: [],
            loading: true,
        }
    },
    created() {
        this.getAlbums();
    },
    methods: {
        getAlbums() {
            // API call
            axios.get(this.apiURL)
            .then(result => {
                this.albums = result.data.response;
                this.loading = false;
            })
            .catch(error => {
                console.log(error);
            });
        },
    },
}
</script>

<style scoped lang="scss">
// Variables
@import '../styles/vars.scss';

main{
    margin: 125px 57.5px 30px;
    // background: rgba(204, 204, 204, 0.37);
    .card-wrapper{
        width: calc(100% / 8);
        padding:0 17.5px;
        &:last-child{
        margin-right: 0;
        }
    }
}
</style>