<template>
    <div id="home">
        <img alt="Vue logo" src="../assets/logo.png"><br>
        <table id="homeHolder" style="position: center">
            <tr>
                <td><ImgHolder nom="venta.png"  holder="Venta"           link="ventas"></ImgHolder></td>
                <td><ImgHolder nom="compra.png" holder="Compra"          link="compras"></ImgHolder></td>
                <td><ImgHolder nom="add.png"    holder="Crear Producto"  link="crearProducto"></ImgHolder></td>
                <td><ImgHolder nom="total.png"  holder="Total Dia"       link="totalDia"></ImgHolder></td>
                <td><ImgHolder nom="search.png"  holder="Buscar"         link="buscarProducto"></ImgHolder></td>
            </tr>
        </table>
    </div><!--'/ventas','/compras','/cierreCaja','/totalDia','/buscarProducto','/agregarProducto'-->
</template>
<script>
    import ImgHolder from "./imgholder"
    export default {
        name: "home",
        components:{
            ImgHolder
        }
    }
</script>

<style scoped>

</style>