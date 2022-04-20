<template>
    <div class="logoContainer">
        <div class="bg-dark logo p-2">
            <img src="./../assets/img/logo-small.svg" alt="">
        </div>
    </div>
</template>

<script>
export default{
    name: 'TopLogo'
}
</script>

<style scoped>
    .logoContainer{
        background-color: #2E3A46;
    }
    .logo{
        height: 80px;
    }
    .logo img{
        height: 100%;
    }
</style>