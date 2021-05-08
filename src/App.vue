<template>
    <div id="app">
        <Header :logo="require('./assets/imges/logo.png')" />
        <Main />
    </div>
</template>

<script>
import Header from "@/components/Header";
import Main from "@/components/Main";

export default {
    name: "App",
    components: {
        Header,
        Main,
    },
};
</script>

<style lang="scss">
// Variables
@import "./styles/vars.scss";
// General styles
@import "./styles/general.scss";
// Utilities
@import "./styles/utilities.scss";
</style>
