<template>
    <div id="app">
        <router-view></router-view>
        <Footer></Footer>
    </div>
</template>

<script>
    import Footer from './Components/Footer'
    export default {
        name: 'App',
        components: {
            Footer
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
    @import './assets/Css/styles.css';  /* importamos la hoja de estilos creada */
</style>