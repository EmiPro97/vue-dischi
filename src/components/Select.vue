<template>
    <div class="select-wrapper">
        <label for="search-genre">Filter by genre:</label>
        <div class="fake-select">
            <select
                @change="$emit('performFilter', currentGenre)"
                v-model="currentGenre"
                @click="openedSelect = !openedSelect"
                name="search-genre"
                id="search-genre"
            >
                <option value="All">All</option>
                <option
                    v-for="(genre, index) in optionsArray"
                    :key="index"
                    :value="genre"
                    >{{ genre }}
                </option>
            </select>
        </div>
        <div :class="!openedSelect ? 'clip' : 'clip closed-clip'"></div>
    </div>
</template>

<script>
export default {
    name: "Select",
    props: {
        optionsArray: Array,
    },
    data() {
        return {
            openedSelect: false,
            currentGenre: "All",
        };
    },
};
</script>

<style scoped lang="scss">
// Variables
@import "../styles/vars.scss";

.select-wrapper {
    position: relative;
    margin: 15px auto;
    width: 300px;
    text-align: center;
    .fake-select {
        display: inline-block;
        margin-left: 10px;
        background-color: $bg-secondary;
        border-bottom: 2px solid #171e24;
        transition: background 1s ease, border-color 1s ease;
        &:hover,
        &:focus {
            color: $main-text;
            background-color: #171e24;
            border-bottom-color: $bg-secondary;
        }
        &:hover ~ .clip,
        &:focus ~ .clip {
            background: $main-text;
        }
    }
    #search-genre {
        position: relative;
        z-index: 1;
        color: #ccc;
        width: 100px;
        outline: none;
        font-size: 15px;
        font-weight: 500;
        cursor: pointer;
        background-color: transparent;
        border: none;
        border-bottom: 2px solid transparent;
        padding: 3px 5px 0;
        appearance: none;
        transition: color 0.4s ease;
        &:hover,
        &:focus {
            color: $main-text;
        }
        option {
            background-color: #171e24;
        }
    }
    .clip {
        width: 10px;
        height: 6px;
        clip-path: polygon(50% 100%, 0 0, 100% 0);
        background: #ccc;
        position: absolute;
        top: 8px;
        right: 50px;
        cursor: pointer;
        transition: background 0.4s ease;
        &.closed-clip {
            clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
        }
    }
}
</style>
