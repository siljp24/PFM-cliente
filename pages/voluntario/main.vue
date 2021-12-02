<template>
    <div class="voluntarios-main">
        <v-row>
            <v-col cols="12">
                <v-flex text-right>
                    <v-btn color="green lighten-2" to="/voluntario/crearAnimal">NUEVO ANIMAL</v-btn>
                </v-flex>
            </v-col>
        </v-row>
        <v-row>
            <div v-for="(animal,index) in animales" :key="index">
            <AnimalCard />
        </div>
        </v-row>
    </div>
</template>

<script>
export default {
    layout:'mainVoluntarios',
    data(){
        return{
            animales:{
                animal1:{},
                animal2:{},
                animal3:{},
                animal4:{},
                animal5:{},
                animal6:{},
            }
        }
    }
}
</script>