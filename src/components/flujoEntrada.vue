<template>
    
</template>
<template>
    <div>
        <h2>Ingreso de productos</h2><router-link to="/home"> Volver </router-link><br><br>
        <div id="addProdFormHolder">
            <form method="get" id="addProdForm"  @submit="processForm">
                <label for="codProd">Codigo del Producto:</label><br>
                <input type="text" id="codProd" name="codProd" v-model="codProd"><br>

                <label for="nomProd">Nombre del producto:</label><br>
                <input type="text" id="nomProd" name="nomProd" v-model="nomProd"><br>

                <label for="cantProd">Cantidad a ingresar:</label><br>
                <input type="text" id="cantProd" name="cantProd" v-model="cantProd"><br>

                <label for="numLote">Numero de Lote:</label><br>
                <input type="text" id="numLote" name="numLote" v-model="numLote"><br>

                <label for="fVenc">Fecha de Vencimiento:</label><br>
                <input type="date" id="fVenc" name="fVenc" v-model="fVenc"><br>

                <label for="proveedor">Proveedor:</label><br>
                <input type="text" id="proveedor" name="proveedor" v-model="proveedor"><br>

                <p>Categoria:</p>
                <select name="catProd" id="catProd" v-model="catProd">>
                    <option value="Vegetales">Vegetales</option>
                    <option value="Bebidas">Bebidas</option>
                    <option value="Ferreteria">Ferreteria</option>
                </select><br>

                <p>Unidad de medida:</p>
                <select name="uMedida" id="uMedida" v-model="uMedida">>
                    <option value="Litros">Litros</option>
                    <option value="Kilos">Kilos</option>
                    <option value="Metros">Metros</option>
                </select><br>

                <label for="desc">Descripcion:</label><br>
                <input type="text" id="desc" name="desc" v-model="desc"><br>
                <br>
                <label for="addProd">Agregar Producto</label><br>
                <input type="submit" value="Submit" id="addProd" name="addProd">
            </form>
        </div>
    </div>
</template>
<script>
    export default {
        name: "flujoEntrada",
        data: function(){
            return {
                nomProd: '',
                codProd: '',
                cantProd: '',
                numLote: '',
                fVenc: '',
                proveedor: '',
                catProd: '',
                uMedida: '',
                desc: '',
            }
        },
        methods: {
            processForm: function() {
                var ingresoProd = {
                    Nombre_Producto:    this.nomProd,
                    Codigo_Producto:    this.codProd,
                    Cantidad_Producto:  this.cantProd,
                    Numero_Lote:        this.numLote,
                    Fecha_Vencimiento:  this.fVenc,
                    Proveedor:          this.proveedor,
                    Categoria:          this.catProd,
                    Unidad_de_medida:   this.uMedida,
                    Descripcion:        this.desc,
                }
                console.log("ingresado:", ingresoProd);
                alert('#########    Datos del producto ingresado    #########'+'\n'+
                    "Nombre: "+ this.nomProd+'\n'+
                    "Codigo: "+ this.codProd+'\n'+
                    "Cantidad: "+ this.cantProd+'\n'+
                    "Lote: "+   this.numLote+'\n'+
                    "Proveedor: "+ this.proveedor+'\n'+
                    "Categoria: "+ this.catProd+'\n'+
                    "Unidad de Medida: "+ this.uMedida+'\n'+
                    "Fecha de vencimiento: "+ this.fVenc+'\n'+
                    "Descripcion: "+ this.desc
                );
            }
        }
    }
</script>
<script>
    export default {
        name: "flujoEntrada"
    }
</script>
