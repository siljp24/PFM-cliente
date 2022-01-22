<template>
  <div class="animal-card">
      <v-card class="ma-6" min-width="344" max-width="344">
        <v-img :src="animal.foto" height="200px" v-on:click="irDiarios(animal._id)"></v-img>
        <v-card-title>{{ animal.nombre }}</v-card-title>
        <v-card-subtitle>{{ animal.especie }}, {{ animal.edad }}</v-card-subtitle>
        <v-card-actions>
          <v-btn color="orange lighten-2" disabled text>Conóceme</v-btn>
          <v-spacer></v-spacer>
          <v-btn icon @click="show = !show">
            <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
          </v-btn>
        </v-card-actions>
        <v-expand-transition>
          <div v-show="show">
            <v-divider></v-divider>
            <v-card-text>{{ animal.descripcion }}</v-card-text>
          </div>
        </v-expand-transition>
      </v-card>
  </div>
</template>

<script>
export default {
  props:{
    animal:{
      type:Object,
      required: true,
    },
  },
    data(){
        return{
          show: false,
        }
    },
    methods:{
      irDiarios(idAnimal){
        this.$router.push(`/voluntario/idAnimal/${idAnimal}`);
      }
    }
}
</script>