<template>
    <div>
    <h2>Ventas</h2><router-link to="/home"> Volver </router-link>
    <!---->
        <br>
        <div id="ventas-holder">
            <div id="table-holder">
                <table class="list-Holder">
                    <tr>
                        <th>Eliminar</th><th>Nombre</th><th>Marca</th><th>Precio Unitario</th><th>Precio Compra</th>
                    </tr>
                    <tr>
                        <td>X</td>
                        <td>Nombre Prod1</td>
                        <td>Marca Prod1</td>
                        <td>PrecioProd1</td>
                        <td>TotalProd1</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                    <tr><td>X</td><td>Nombre Prod2</td><td>Marca Prod2</td><td>PrecioProd2</td><td>TotalProd2</td>
                    </tr>
                </table>
            </div>
            <div id="detail-holder">
                <table class="detail-list">
                    <tr>
                        <th colspan="2">Detalle Compra</th>
                    </tr>
                    <tr>
                        <td>Total Compra</td><td>$123123</td>
                    </tr>
                    <tr>
                        <td>Descuentos</td><td>$12312</td>
                    </tr>
                    <tr>
                        <td>Impuestos</td><td>$12312</td>
                    </tr>
                </table>
                <br>
                <h3>Total a pagar:</h3>
                <div><p>$123123</p></div>
                <h3>Pago Cliente:</h3>
                <div><p>$130000</p></div>
            </div>
            <div id="button-holder">
                <div id="opcCompra">
                <form>
                    <button id="btn1">Confirmar Compra</button>
                    <button id="btn2">Limpiar Lista</button>
                    <button id="btn3">Anular Compra</button>
                </form>
                </div>
                <div id="prodManual">
                    <form>
                    <label for="codprod">Codigo Producto:</label><br>
                    <input type="text" id="codprod" name="codprod"><br>
                    <label for="cantprod">Cantidad:</label><br>
                    <input type="number" id="cantprod" name="cantprod">
                    <button id="btnManual">Agregar Producto</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ventas"
    }
</script>
