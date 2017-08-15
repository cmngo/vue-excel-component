<template>
    <div id="app">
        <excel></excel>
    </div>
</template>

<script>
    import Hello from './components/Hello';
    import Excel from './components/excel';

    export default {
        name: 'app',
        components: {
            Hello,
            Excel
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
