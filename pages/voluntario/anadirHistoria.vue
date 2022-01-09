<template>
    <div class="voluntario-anadir-historia">
        <v-row>
            <v-col cols="2">
                <v-btn v-on:click="goBack" block color="deep-orange lighten-3">VOLVER</v-btn>
            </v-col>
            <v-col cols="10"></v-col>
        </v-row>
        <v-row>
            <v-col md="6" offset-md="3"><AnadirHistoria /></v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    layout: 'crearEditarHistoria',
    methods:{
        goBack(){
           const idAnimal = window.localStorage.getItem('idAnimal');
           this.$router.push(`/voluntario/idAnimal/${idAnimal}`);
           window.localStorage.removeItem('idAnimal');
        },
    }
}
</script>