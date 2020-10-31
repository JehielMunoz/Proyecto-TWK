<template>
    <div class="row">
        <div class="column">
            <form action="action.php" method="post">
                <label for="fname">First Name</label>
                <input type="text" id="fname" name="firstname" placeholder="Nombre">
                <label for="lname">Last Name</label>
                <input type="text" id="lname" name="lastname" placeholder="apellido">
            </form>
        </div>
        <h2>Contactos</h2>
        <ul v-for="cont in contacto" :key="cont">
            <p>{{cont}}</p>
        </ul>
        <input v-model="agregarCont" type="string"/>
        <button v-on:click="agregarC">Agregar Contacto</button>
        <input v-model="EliminarCont" type="string"/>
        <button v-on:click="EliminarC">Eliminar Contacto</button>
    </div>
</template>

<script>
    export default {
        name: "contacto.vue",
        data(){
            return{
                agregarCont:'',
                EliminarCont:'',
                contacto:[''],
            }
        },
        methods: {
            agregarC(){
                this.contacto.push(this.agregarCont)
            },
            EliminarC(){
                this.contacto.pop(this.EliminarCont)
            },
        },
    }
</script>

<style scoped>

</style>