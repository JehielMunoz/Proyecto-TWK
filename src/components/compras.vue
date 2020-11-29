<template>
    <div id="app">
        <h2>Compras (Reabastecimiento)</h2><router-link to="/home"> Volver </router-link><br>
        <div id="table-holder" style="width:55%;left:5%">
            <table class="list-Holder">
                <thead>
                <th>N°</th>
                <th>Nombre Producto</th><th>Marca Producto</th>
                <th>Precio Unitario</th><th>Cantidad Solicitada</th>
                </thead>
                <tr v-for="prod in productos" :key='prod.indx' >
                    <td>{{ prod.indx +1}}    </td>
                    <td>{{ prod.nomProd }}</td>
                    <td>{{ prod.marProd }}</td>
                    <td>{{ prod.preProd }}</td>
                    <td>{{ prod.cntProd }}</td>
                    <td><button v-on:click="delItem(prod)">Eliminar Producto</button></td>
                </tr>
            </table>
            <br><p>{{productos}}</p>
        </div>
        <div id="inputHolder" style="right:5%;position: fixed;">
            <input v-model="nomProd" type="string" placeholder="Nombre del Producto"/>
            <input v-model="marProd" type="string" placeholder="Marca del producto"/>
            <input v-model="cntProd" type="string" placeholder="Cantidad a ingresar"/>
            <button v-on:click="addItem">Agregar Producto</button>
            <form method="get" @submit="processForm">
                <label>Enviar Solicitud</label>
                <input type="submit" name="reqProd" id="reqProd" value="Submit">
            </form>
        </div>

    </div>
</template>

<script>
    export default {
        name: "compras",
        data: function(){
            return {
                indx:0,
                nomProd: '',
                marProd: '',
                preProd: '',
                cntProd: '',
                productos: []
            }
        },
        methods:{
            addItem(){
                var producto ={
                    nomProd:this.nomProd,   marProd: this.marProd,
                    preProd:this.preProd,   cntProd: this.cntProd,
                    indx:this.indx
                };
                console.log("nuevo registrto",this.indx,producto)
                this.productos.push(producto)
                this.nomProd = '';  this.marProd = '';
                this.preProd = '';  this.cntProd = '';
                this.indx    = this.indx+1;
            },
            delItem(prod) {
                var indice = this.productos.indexOf(prod);
                if (indice != -1) {
                    this.productos.splice(indice, 1);
                }
                if(this.productos.length==0){
                    this.indx=0;
                }
                console.log(this.indx)
            },
            processForm: function() {
                console.log({
                    Nombre_Producto:    this.nomProd,
                    Codigo_Producto:    this.codProd,
                    Marca_Producto:     this.marProd,
                    Precio_Producto:    this.preProd,
                    CantidadSolicitada: this.cntProd,
                });
                alert('Enviado!');
            }
        }
    }
</script>

<style scoped>

</style>