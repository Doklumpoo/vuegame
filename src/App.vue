<template>
<div id="app">
    <!--<HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <Game />
</div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Game from './components/Game'
export default {
    name: 'App',
    components: {
        Game,
    }
}
</script>

<style>
#app {

    background-image: url(https://pbs.twimg.com/media/CmPANjwWUAEpa3b.jpg);
    height: 100%;
    background-size: cover;
    background-repeat: no-repeat;
    position: relative;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: auto;
    padding: 50px;
}
</style>
