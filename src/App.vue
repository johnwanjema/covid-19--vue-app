<template>
    <div id="app">
        <p>wanjema</p>
        <div class="container">
            <div class="row">
                <div class="col-md-12">
                    <google-map />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import GoogleMap from "./components/map";

export default {
    components: {
        GoogleMap
    },
    name: 'App',
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
