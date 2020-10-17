<template>
    <div>
        <img id="img-holder" :src="require(`../assets/icons/${nom}`)"><br>
        <router-link :to="`${link}`">{{holder}}</router-link>
    </div>
</template>

<script>
    export default {
        name: "img-holder",
        props: {
            nom: String,
            holder: String,
            link: String
        }
    }
</script>