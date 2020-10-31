<template>
    <div>
        <h2>Componente HOME</h2>
        <p><b>Parrafo en negrita</b></p>
        <p> parrafo sin negrita</p>
        <p class="clase-1">parrafo con estilo</p>
        <br>
        <contacto></contacto>
    </div>
</template>

<script>
    import contacto from "./contacto"
    export default {
        name: "home.vue",
        components:{
            contacto
        }
    }
</script>

<style scoped>
.clase-1{
    background-color: aqua;
    text-blink: on;
}
</style>