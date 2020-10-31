<template>
    <div id="app">
        <h2>Compras</h2><router-link to="/home"> Volver </router-link>
        <div id="table-holder">
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
        </div>
        <div id="inputHolder">
            <input v-model="nomProd" type="string"/>
            <input v-model="marProd" type="string"/>
            <input v-model="preProd" type="string"/>
            <input v-model="cntProd" type="string"/>
            <button v-on:click="addItem">Agregar Producto</button>
        </div>
        <br><br><br><br><p>{{productos}}</p>
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
                /*this.productos.splice(this.prod.indexOf(prod),1);
                if(this.productos.length==0){
                    this.indx=0;
                }
                this.productos.pop() console.log(productos);this.indx = ind,ind*/
                console.log(this.indx)
            }
        }
    }
</script>

<style scoped>

</style>