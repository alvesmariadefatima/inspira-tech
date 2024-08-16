<template>
    <footer>Desenvolvido por <a href="https://github.com/alvesmariadefatima" target="_blank">@alvesmariadefatima</a> 👩🏻‍💻</footer>
</template>

<script>
export default {
    name: "Footer",
}
</script>

<style scoped>
    footer {
        font-family: "Englebert", cursive;
        text-align: center;
    }

    a {
        text-decoration: none;
        color: black;
    }

    a:hover {
        color: #FF1493;
        transition: .5s;
    }
</style>