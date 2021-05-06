<template>
    <a href="#" class="info-wrap flex f-column items-center">
        <div class="img-wrap"><img :src="infos.poster" :alt="infos.title"></div>
        <h3 class="album-title">{{infos.title}}</h3>
        <div class="album-author">{{infos.author}}</div>
        <div class="production-year">{{infos.year}}</div>
        <div class="music-style">{{infos.genre}}</div>
    </a>
</template>

<script>

export default {
    name: 'Card',
    props: ['infos'],
}
</script>

<style scoped lang="scss">
// Variables
@import '../styles/vars';

.info-wrap{
    height: 100%;
    background: $bg-secondary;
    padding: 20px;
    cursor: pointer;
    transition: transform 0.4s ease-out;
    &:hover{
        transform: scale(1.05);
    }
    .img-wrap{
        height: 150px;
        margin-bottom: $inner-margin-big;
        img{
            width: 100%;
            height: 100%;
        }
    }
    .album-title{
        text-transform: uppercase;
        text-align: center;
        margin-bottom: $inner-margin-big;
    }
    .album-author{
        font-size: 18px;
    }
    .album-author,
    .production-year{
        color: $secondary-text;
        font-weight: 500;
        margin-bottom: $inner-margin-small;
    }
    .music-style{
        color: $main-text;
        font-weight: 500;
    }
}
</style>