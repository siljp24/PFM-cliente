<template>
    <div class="voluntario-idAnimal">
        <v-row>
           <v-col cols="6">
                <v-flex text-left>
                    <v-btn color="orange lighten-2" to="/voluntario/editarAnimal">EDITAR ANIMAL</v-btn>
                </v-flex>
            </v-col>
            <v-col cols="6">
                <v-flex text-right>
                    <v-btn color="green lighten-2" to="/voluntario/anadirHistoria">Nueva historia</v-btn>
                </v-flex>
            </v-col>
        </v-row>
        <v-row>
            <div v-for="(diario,index) in diarios" :key="index">
                <DiarioCard />
            </div>
        </v-row>
       
    </div>
</template>

<script>
export default {
    layout: 'animal',
    data(){
        return{
            diarios:{
                diario1:{},
                diario2:{},
                diario3:{},
                diario4:{},
                diario5:{},
                diario6:{},
            }
        }
    }
}
</script>