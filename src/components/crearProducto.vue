<template>
    <div id="main">
        <h2>Crear producto</h2><router-link to="/home"> Volver </router-link><br><br>
        <p v-if="loading">Cargando...</p>
        <div id="addProdFormHolder" v-else style="position: center">
            <form method="POST" name="newProd" id="addProdForm"  @submit.prevent="processForm">
                <h3>Codigo Producto:{{maxId}}</h3><br>
                <input hidden type="text" id="respC" name="respC" v-model="respCreacion">
                <label for="nomProd">Nombre del producto:</label>
                <input type="text" id="nomProd" name="nomProd" v-model="nomProd"><br>
            <table id="selectCrearHolder">
                <tr>
                    <th>
                        <p>Proveedor:</p>
                    </th>
                    <td>
                        <select name="proveedor" id="prov" v-model="provSelect">
                            <option v-for="prov in proveedores" :key="prov.id" :value="prov.id">{{prov.razonSocial}}</option>
                        </select>
                    </td>
                    <th>
                        <p>Marca:</p>
                    </th>
                    <td>
                        <select name="uMedida" id="Marca" v-model="marcaSelect">
                            <option v-for="marca in marcas" :key="marca.id" :value="marca.id">{{marca.descripcion}}</option>
                        </select>
                    </td>
                </tr>
                <tr>
                    <th>
                        <p>Categoria:</p>
                    </th>
                    <td>
                        <select name="catProd" id="catProd" v-model="catSelect">
                            <option v-for="cat in categorias" :key="cat.id" :value="cat.id">{{cat.descripcion}}</option>
                        </select>
                    </td>
                    <th>
                        <p>Unidad de medida:</p>
                    </th>
                    <td>
                        <select name="uMedida" id="uMedida" v-model="medidaSelect">
                            <option v-for="med in uMedidas" :key="med.id" :value="med.id">{{med.descripcion}}</option>
                        </select>
                    </td>
                </tr>
                <tr>
                    <th>
                        <label for="desc">Descripcion:</label>
                    </th>
                    <td>
                        <input type="text" id="desc" name="desc" v-model="desc">
                    </td>
                </tr>
                <tr>
                    <th><input type="submit" value="Agregar Producto" id="addProd" name="addProd"></th>
                </tr>
            </table>
            </form>
            <button @click="forceRerender()">Actualizar</button>
            <button @click="restoreAutoIncrement()">Restaurar auto increment</button>
        </div>
        <!--<br><br><br><p v-if="hasError">oopppS</p><p v-else></p>:key="respuesta"
            <p>lista completa: {{nuevoProducto}}</p>-->
    </div>
</template>
<script>
    import axios from "axios";

    export default {
        name: "agregarProducto",
        data: function(){
            return {
                maxId:0,         marcaSelect:'',catSelect:'',
                medidaSelect:'', provSelect:'',
                marcas:[], categorias:[], uMedidas:[],proveedores:[], productos:[],nuevoProducto:[],
                nomProd: '',    respCreacion:4,
                codProd: '',    cantProd: '',
                numLote: '',    fVenc: '',
                proveedor: '',  marca:'',
                catProd: '',    uMedida: '',
                desc: '',       timeStamp: '',
                loading:true,hasError:false, error:false, respuesta:0,
                }
            },
        methods: {
            getNow: function() {
                const today = new Date();
                const date = today.getFullYear()+'-'+(today.getMonth()+1)+'-'+today.getDate();
                const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
                const dateTime = date +' '+ time;
                return this.timeStamp = dateTime;
            },
            forceRerender(){window.location.reload();
                //this.respuesta+=1;
                //console.log(this.respuesta);
                //$("#addProdFormHolder").load(window.location.href + " #addProdFormHolder" );
                //this.$forceUpdate();
                /*if(respuesta==1){
                    alert('Producto Creado!');
                    location.reload();
                    respuesta=0;
                }*/
            },
            processForm: function() {
                this.respuesta=false;
                const nuevoProducto = {
                    nombre:             this.nomProd,
                    idCategoria:        this.catSelect,
                    idMarca:            this.marcaSelect,
                    idMedida:           this.medidaSelect,
                    descripcion:        this.desc,
                    Proveedor:          this.provSelect,
                    idresponsableCreacion: this.respCreacion,
                    fechaCreacion: this.getNow()
                }/**/;
                this.nuevoProducto.push(nuevoProducto);
                console.log("fecha",this.getNow(),nuevoProducto);
                axios.post('http://127.0.0.1:8000/api/crearProducto/', nuevoProducto);
                    //.then(response => {this.respuesta+=response.data});
                if(this.respuesta==1){window.location.reload()}
                    //this.respuesta+=1;//.finally(this.respuesta+=1);
                    //.catch(error => this.hasError = true);
            },
            restoreAutoIncrement: function () {
                axios.get('http://127.0.0.1:8000/api/restoreAA').finally(window.location.reload());
            }
        },
        mounted() {
            axios
                .get('http://127.0.0.1:8000/api/maxId')
                .then(response => (this.maxId = response.data));
            axios.get('http://127.0.0.1:8000/api/proveedores')
                .then(response => (this.proveedores = response.data.data));
            axios.get('http://127.0.0.1:8000/api/marcas')
                .then(response => (this.marcas = response.data.data));
            axios.get('http://127.0.0.1:8000/api/categorias')
                .then(response => (this.categorias = response.data.data));
            axios.get('http://127.0.0.1:8000/api/medidas')
                .then(response => (this.uMedidas = response.data.data))
                .finally(() => this.loading = false);
        }
    }
</script>