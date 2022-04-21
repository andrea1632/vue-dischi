<template>
    <div class="col mx-4 mb-4 spotiCard align-items-center d-flex flex-column">
        <div class="photoContainer">
            <img :src="image" :alt="author" class="h-100 m-auto mt-4">
        </div>
        <h4 class="text-white text-center mt-5">
            {{title}}
        </h4>
        <div class="text-secondary text-center">
            {{author}} <br>
            {{year}}
        </div>
    </div>
</template>

<script>
    export default{
        name: 'CardComp',
        props: ['image', 'title', 'author', 'year',]
    }
</script>

<style scoped>
    .spotiCard{
        background-color: #2E3A46;
    }
    .photoContainer{
        height: 150px;
        width: 150px;
    }
</style>