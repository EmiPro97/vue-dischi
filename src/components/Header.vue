<template>
  <header>
      <a class="logo-wrap" href="#">
          <img :src="logo" alt="logo"/>
      </a>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: ['logo'],
}
</script>

<style scoped lang="scss">
// Variables
@import '../styles/vars.scss';

header{
    padding: 15px;
    background: $bg-secondary;
    .logo-wrap{
        display: block;
        width: 50px;
        height: 50px;
        img{
            width: 100%;
            height: 100%;
        }
    }
}
</style>