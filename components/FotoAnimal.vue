<template>
    <div class="fotoDelAnimal ">
        <v-row class="d-flex justify-center my-5">
            <v-img class="foto-animal" :src="animal.foto" max-height="150px" min-height="150px" min-width="150px" max-width="150px"></v-img>
        </v-row>
        <v-row class="d-flex justify-center my-5">
        <h3>{{animal.nombre}}</h3>

        </v-row>
    </div>
</template>

<script>
export default {
    props:{
        animal:{
            type:Object,
            required:true,
        }
    },
}
</script>

<style>
.foto-animal{
    border-radius: 50%;
    text-align: center;
    
}


</style>