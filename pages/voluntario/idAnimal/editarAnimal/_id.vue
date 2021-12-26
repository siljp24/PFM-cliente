<template>
    <div class="voluntario-editar-animal">
        <v-row>
            <v-col cols="2">
                <v-btn to="/voluntario/idAnimal" block color="deep-orange lighten-3">VOLVER</v-btn>
            </v-col>
        </v-row>
         <v-row>
            <v-col md="6" offset-md="3">
                <EditarAnimal />
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    layout: 'crearEditarAnimal',
    
}
</script>