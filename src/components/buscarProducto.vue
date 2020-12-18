<template>
    <div>
        <h2>Buscar Productos</h2><router-link to="/home"> Volver </router-link><br><br>
        <!--<h1 :v-if="hasError">ERROR</h1>
        <h1 :v-if="loading">Cargando...</h1>-->
        <div style="left: 63%">
            <form method="GET" @submit.prevent="processForm">
                <table id="buscaHolder">
                    <tr>
                        <th>
                            <button id="allProd" style="width:150px;height:25px; left:22%;" @click="allProd()">Mostrar Todo</button>
                        </th>
                        <th>
                            <button id="cleanList" style="width:150px;height:25px; left:22%;" @click="cleanList()">Limpiar Lista</button>
                        </th>
                    </tr>
                    <tr>
                        <th>
                            <button id="codProd" style="width:150px;height:25px; left:22%;" @click="buscaCod(codProd)">Buscar Codigo</button>
                        </th>
                        <th>
                            <input v-model="codProd" type="number" placeholder="Codigo Producto"/>
                        </th>
                    </tr>
                    <tr>
                        <th>
                            <button id="nomProd" style="width:150px;height:25px; left:22%;" @click="buscaNom(nomProd)">Buscar Producto</button>
                        </th>
                        <th>
                            <input v-model="nomProd" type="text" placeholder="Nombre Producto"/><br>
                        </th>
                    </tr>
                </table>
            </form>
        </div>
        <div>
            <table id="fullListTable">
                <thead>
                    <th>Codigo</th>
                    <th>Nombre</th>
                    <th>Categoria</th>
                    <th>Unidad de medida</th>
                    <th>Marca</th>
                    <th>Responsable</th>
                    <th>Descripcion</th>
                    <th>Creacion</th>
                    <th>Modificacion</th>
                    <th>Eliminar</th>
                    <th>Ingresar Producto</th>
                </thead>
                <tr v-for="producto in productos" :key="producto.codigo">
                    <td>{{producto.codigo}}</td>
                    <td>{{producto.nombre}}</td>
                    <td>{{producto.idCategoria}}</td>
                    <td>{{producto.idMedida}}</td>
                    <td>{{producto.idMarca}}</td>
                    <td>{{producto.idresponsableCreacion}}</td>
                    <td>{{producto.descripcion}}</td>
                    <td>{{producto.fechaCreacion}}</td>
                    <td>{{producto.fechaModificacion}}</td>
                    <td><button id="borrarProducto" @click="delProducto(producto)">X</button></td>
                    <td><button id="ingresarProducto" @click="addProducto(producto)">-+-</button></td>
                </tr>
            </table>


            <table id="addProd" v-if="addProductoConfirm">
                <thead>
                <th>Codigo</th>
                <th>Nombre</th>
                <th>Categoria</th>
                <th>Unidad de medida</th>
                <th>Marca</th>
                <th>Responsable</th>
                <th>Descripcion</th>
                <th>Creacion</th>
                <th>Modificacion</th>
                </thead>
                <tr>
                    <td>{{addProd.codigo}}</td>
                    <td>{{addProd.nombre}}</td>
                    <td>{{addProd.idCategoria}}</td>
                    <td>{{addProd.idMedida}}</td>
                    <td>{{addProd.idMarca}}</td>
                    <td>{{addProd.idresponsableCreacion}}</td>
                    <td>{{addProd.descripcion}}</td>
                    <td>{{addProd.fechaCreacion}}</td>
                    <td>{{addProd.fechaModificacion}}</td>
                    <td><button id="confAddProducto" @click="addProducto(producto)">X</button></td>
                </tr>
            </table>

        </div>
        <!--<br><br><br><p>lista completa: {{productos}}</p>-->
    </div>
</template>

<script>
    import axios from 'axios';
    export default {
        name: "buscarProducto",
        data: function() {
            return {
                productos: [], addProd:[],
                hasError: false,
                addProductoConfirm:false,
                loading: true,
                codProd:  0,
                nomProd: '',
                //marProd: '',                preuProd: 0,                totalProd: 0,
                //sumaCompra: 0,              totalCompra: 0,             descuentos: 1222,
                //impuestos: 0,               vueltoCliente:0,
                //pagoCliente:0,
            }
        },
        methods:{
            buscaNom(nombre){
                axios.get('http://127.0.0.1:8000/api/buscarNombre/' + nombre)
                    .then(response=>(this.productos=response.data.data));
                console.log('productos',this.productos);
            },
            buscaCod(codigo){
                axios.get('http://127.0.0.1:8000/api/buscarCodigo/' + codigo)
                    .then(response=>(this.productos=response.data.data));
                console.log('productos',this.productos);
            },
            allProd(){
                axios.get('http://127.0.0.1:8000/api/buscar/')
                    .then(response=>(this.productos=response.data.data))
            },
            delProducto(codigo){
                codigo=codigo.codigo;
                console.log(codigo);
                axios.get('http://127.0.0.1:8000/api/eliminar/' + codigo);
                //window.location.reload();
                //.then(response=>(this.productos=response.data.data))
            },
            addProducto(codigo){
                this.addProductoConfirm = true;
                codigo=codigo.codigo;
                console.log(codigo);
                axios.get('http://127.0.0.1:8000/api/ingresarProducto/' + codigo)
                    .then(response=>(this.productos=response.data.data));
                //window.location.reload();
                //FALTA TODO CONTROLER
                //.then(response=>(this.productos=response.data.data))
            },
            cleanList: function(){
                if(this.productos.length!=0){
                    this.productos=[];
                }
            },

            processForm: function() {
                console.log("Consulta enviada");
            }
        }
    }
</script>