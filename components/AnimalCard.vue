<template>
  <div class="animal-card">
      <v-card class="ma-6" max-width="344">
        <v-img :src="animal.foto" height="200px" v-on:click="irDiarios"></v-img>
        <v-card-title>{{ animal.nombre }}</v-card-title>
        <v-card-subtitle>{{ animal.especie }}, {{ animal.edad }}</v-card-subtitle>
        <v-card-actions>
          <v-btn color="orange lighten-2" text>Conóceme</v-btn>
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
    // perfilAnimal:{
    //   type: String,
    // },
    // nombre:{
    //   type: String,
    // },
    // especie:{
    //   type: String,
    // },
    // descripcion:{
    //   type:String,
    //   default: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed convallis, risus a elementum tincidunt, leo magna aliquam ligula, vitae accumsan dui sem non orci. Pellentesque tristique fermentum congue. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Vivamus nisl ipsum, condimentum vel diam quis, hendrerit dictum nulla. Etiam nibh lorem, luctus quis bibendum vitae, facilisis vitae nibh. Ut dignissim ipsum in neque facilisis tincidunt. Nullam sit amet venenatis ante, eget interdum elit. Duis aliquam urna eget est consequat mattis. Vivamus ac sem vel justo laoreet euismod. Donec non tincidunt neque, sit amet convallis tortor.',
    // },
    // edad:{
    //   type: Number,
    // }
  },
    data(){
        return{
          show: false,
        }
    },
    methods:{
      irDiarios(){
        this.$router.push("/voluntario/idAnimal/");
      }
    }
}
</script>