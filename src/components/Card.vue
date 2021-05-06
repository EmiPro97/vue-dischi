<template>
    <div class="info-wrap flex f-column items-center">
        <div class="img-wrap"><img src="https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg" alt="music album"></div>
        <h2 class="album-title"></h2>
        <div class="album-author"></div>
        <div class="production-year"></div>
        <div class="music-style"></div>
    </div>
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
    background: $bg-secondary;
    padding-top: 20px;
    margin-top: 15px;
    .img-wrap{
        width: 80%;
        height: 150px;
        img{
            width: 100%;
            height: 100%;
        }
    }
}
</style>