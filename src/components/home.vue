<template>
    <div id="home">
        <img alt="Vue logo" src="../assets/logo.png">
        <ImgHolder nom="venta.png"  holder="Venta"              link="ventas"></ImgHolder>
        <ImgHolder nom="compra.png" holder="Compra"             link="compras"></ImgHolder>
        <ImgHolder nom="add.png"    holder="Agregar Producto"   link="agregarProducto"></ImgHolder>
        <ImgHolder nom="total.png"  holder="Total Dia"          link="totalDia"></ImgHolder>
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