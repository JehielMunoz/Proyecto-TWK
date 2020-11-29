<template>
    <div>
    <h2>Ventas</h2><router-link to="/home"> Volver </router-link>
    <!---->
        <div id="ventas-holder">
            <div id="table-holder">
                <table class="list-Holder">
                    <thead>
                    <tr>
                        <th>Eliminar</th><th>Cantidad</th><th>Nombre</th><th>Marca</th><th>Precio Unitario</th><th>Precio Compra</th>
                    </tr>
                    </thead>
                    <tr v-for="prod in productosVenta" :key='prod.indx' >
                        <td><button v-on:click="delItem(prod)">X</button></td>
                        <td>{{ prod.cantProd }}</td>
                        <td>{{ prod.nomProd }}</td>
                        <td>{{ prod.marProd }}</td>
                        <td>{{ prod.preuProd }}</td>
                        <td>{{ prod.totalProd }}</td>
                    </tr>
                </table>
            </div>
            <div id="detail-holder">
                <table class="detail-list">
                    <tr>
                        <th colspan="2">Detalle Compra</th>
                    </tr>
                    <tr>
                        <td>Total Compra</td><td> ${{totalCompra}}</td>
                    </tr>
                    <tr>
                        <td>Descuentos</td><td>WIP</td>
                    </tr>
                </table>
                <br>
                <div>
                    <h3>Total a pagar:</h3>
                    <p>${{totalCompra}}</p>

                    <h3>Pago Cliente:</h3>
                    <input v-model="pagoCliente" type="number" placeholder="Ingrese pago"/>
                    <button id="pagoCliente" v-on:click="vueltoClienteFunc">Confirmar Pago</button>
                    <h3>Vuelto Cliente:</h3>
                    <p>${{ vueltoCliente }}</p>
                </div>
            </div>
            <div id="button-holder">
                <div id="opcCompra">
                <form method="POST" @submit.prevent="processForm">
                    <button id="btn1" v-on:click="totalBoleta">Confirmar Compra</button>
                </form>
                    <button id="btn3" v-on:click="cleanList">Anular Compra</button>
                </div>
                <div id="inputHolder" style="left: 63%">

                    <label for="codProd">Codigo Producto:</label><br>
                    <input v-model="codProd" type="number" placeholder="Codigo Producto"/><br>

                    <label for="cantProd">Cantidad:</label><br>
                    <input v-model="cantProd" type="number" placeholder="Cantidad"/><br>
                    <button id="addItm" style="width:150px;height:25px; left:22%;" @click="updateVenta">Agregar Producto</button> <!--  id="btnManual" -->
                    <!--br><p>Codigo producto:{{codProd}} Cantidad producto: {{cantProd}}</p-->
                </div>
            </div>
        </div><!--br><br><br><p>lista completa: {{productosVenta}}</p>-->
    </div>
</template>

<script>
    export default {
        name: "ventas",
        data: function() {
            return {
                codProd:  0,                cantProd: 1,                nomProd: '',
                marProd: '',                preuProd: 0,                totalProd: 0,
                sumaCompra: 0,              totalCompra: 0,             descuentos: 1222,
                impuestos: 0,               productosVenta: [],         vueltoCliente:0,
                pagoCliente:0,
            }
        },
        methods:{
            addItem(){
                if(this.codProd == 1) {
                    var producto = {/*
                        nomProd:this.nomProd,   marProd: this.marProd,
                        preProd:this.preProd,   cntProd: this.cntProd,
                        indx:this.indx
                        */
                        codProd: this.codProd,
                        nomProd: 'prod1', marProd: 'marca1',
                        preuProd: 1200, totalProd: 0,
                        cantProd: this.cantProd
                    };
                }
                if(this.codProd == 2){
                    producto = {
                        nomProd: 'prod2', marProd: 'marca2',
                        preuProd: 200, totalProd: this.preuProd * this.cantProd,
                        cantProd: this.cantProd
                    };
                }
                if(this.codProd == 3){
                    producto = {
                        nomProd: 'prod3', marProd: 'marca3',
                        preuProd: 4200, totalProd: this.preuProd * this.cantProd,
                        cantProd: this.cantProd
                    };
                }
                producto.totalProd= producto.preuProd * this.cantProd;
                console.log("nuevo registro",this.indx,producto);
                this.productosVenta.push(producto);
                console.log("pushProdVenta",this.indx,this.productosVenta);
            },
            cleanList: function(){
                if(this.productosVenta.length!=0){
                    this.productosVenta=[]; this.totalCompra=0; this.sumaCompra=0;
                }
            },
            delItem(prod) {
                var indice = this.productosVenta.indexOf(prod);
                if (indice != -1) {
                    this.productosVenta.splice(indice, 1);
                }
                console.log(prod);
            },
            totalBoleta: function(){
                var aux=0;
                for(var x=0; x <= this.productosVenta.length - 1;x++)
                {
                    aux+= this.productosVenta[x].totalProd
                }
                this.totalCompra=aux;
                return this.totalCompra;
            },
            vueltoClienteFunc: function(){
                this.vueltoCliente = this.pagoCliente - this.totalCompra;
                if(this.vueltoCliente>0){alert('Compra lista, entregue vuelto.'); return this.vueltoCliente;}
                else{alert('Falta dinero!');return false;}
            },
            updateVenta: function(){
              this.addItem();this.totalBoleta();
            },
            processForm: function() {
                console.log("Boleta: ", this.productosVenta,"Total:", this.totalCompra);
                alert('Enviado!');
            }
        }

    }
</script>
