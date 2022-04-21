<template>
    <div class="logoContainer d-flex justify-content-between align-items-center">
        <div class="bg-dark logo p-2">
            <img class="img-fluid rounded-circle" src="./../assets/img/logo-small.svg" alt="">
        </div>
        <div>
            <select v-model="selected" @change="$emit('activeGenre', selected)" class="form-select" name="genere" id="genere">
                <option disabled selected value> -- select an option -- </option>
                <option value="tutti">Tutti</option>
                <option value="rock">Rock</option>
                <option value="pop">Pop</option>
                <option value="jazz">Jazz</option>
                <option value="metal">Metal</option>
            </select>
        </div>
    </div>
</template>

<script>
export default{
    name: 'TopLogo',
    data(){
        return{
            selected: '',
        }
    }
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