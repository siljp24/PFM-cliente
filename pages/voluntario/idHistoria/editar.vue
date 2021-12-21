<template>
    <div class="voluntario-idHistoria-editar">
        <v-row>
            <v-col cols="2">
                <v-btn v-on:click="diario" block color="deep-orange lighten-3">DIARIO</v-btn>
            </v-col>
            <v-col cols="10"></v-col>
        </v-row>
        <v-row>
            <v-col md="6" offset-md="3"><EditarHistoria /></v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    layout:'crearEditarHistoria',
    methods:{
        diario(){
            const idAnimal = localStorage.getItem('idAnimal');
            this.$router.push(`/voluntario/idAnimal/${idAnimal}`);
            localStorage.removeItem('idAnimal');
            localStorage.removeItem('idDiario');
        }
    }
}
</script>