<template>
    <div id="app">
        <h1>nuevo texto por componente</h1>
        <h1>{{ message }}</h1>
    </div>
</template>
<script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.1/vue.min.js"></script>
<script src="./app.vue"></script>
<script>
    new Vue({
        el: '#app',
        data: {texto: ''}
    },
    Vue.component('test',{
        name: "test",
        props: ['message']}))
</script>
<style scoped></style>