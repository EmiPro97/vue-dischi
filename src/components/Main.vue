<template>
    <main>
        <Select :optionsArray="optionsArray" @performFilter="getCurrentGenre" />
        <div v-if="!loading" class="flex f-wrap justify-center">
            <div
                v-for="(album, index) in filteredOptions"
                :key="index"
                class="card-wrapper"
            >
                <Card :infos="album" />
            </div>
        </div>
        <div v-else class="loading">Loading...</div>
    </main>
</template>

<script>
import Card from "./Card";
import axios from "axios";
import Select from "./Select";

export default {
    name: "Main",
    components: {
        Card,
        Select,
    },
    data() {
        return {
            apiURL: "https://flynn.boolean.careers/exercises/api/array/music",
            albums: [],
            loading: true,
            errorFound: false,
            optionsArray: [],
            currentGenre: "All",
        };
    },
    created() {
        this.getAlbums();
    },
    computed: {
        filteredOptions() {
            if (this.currentGenre === "All") {
                return this.albums;
            }
            return this.albums.filter(
                (element) => element.genre === this.currentGenre
            );
        },
    },
    methods: {
        getAlbums() {
            // API call
            axios
                .get(this.apiURL)
                .then((result) => {
                    this.albums = result.data.response;
                    this.loading = false;
                })
                .catch((error) => {
                    console.log(error);
                    this.errorFound = true;
                })
                .finally(() => {
                    if (!this.errorFound) {
                        this.getOptions();
                    }
                });
        },
        getOptions() {
            this.albums.forEach((element) => {
                if (!this.optionsArray.includes(element.genre)) {
                    this.optionsArray.push(element.genre);
                }
            });
        },
        getCurrentGenre(genre) {
            this.currentGenre = genre;
        },
    },
};
</script>

<style scoped lang="scss">
// Variables
@import "../styles/vars.scss";

main {
    margin: 100px 57.5px 30px;
    min-height: 400px;
    .card-wrapper {
        width: calc(100% / 8);
        min-height: 379px;
        padding: 0 17.5px;
        margin-top: 15px;
    }
}
</style>
