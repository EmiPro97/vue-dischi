<template>
    <div class="select-wrapper">
        <label for="search-genre">Filter by genre:</label>
        <select name="search-genre" id="search-genre">
            <option value="all">All</option>
            <option value=""></option>
        </select>
        <div class="clip"></div>
    </div>
</template>

<script>
export default {
    name: "Select",
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
    #search-genre {
        position: relative;
        color: #ccc;
        width: 100px;
        margin-left: 10px;
        outline: none;
        font-size: 15px;
        font-weight: 500;
        cursor: pointer;
        background-color: $bg-secondary;
        border: none;
        border-bottom: 2px solid #171e24;
        padding: 3px 5px 0;
        appearance: none;
        transition: background 0.3s ease, border-color 0.3s ease, color 0.3s ease;
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
    .clip {
        width: 10px;
        height: 6px;
        clip-path: polygon(50% 100%, 0 0, 100% 0);
        background: #ccc;
        position: absolute;
        top: 8px;
        right: 50px;
        cursor: pointer;
        transition: background 0.3s ease;
    }
}
</style>
