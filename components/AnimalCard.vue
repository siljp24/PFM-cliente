<template>
  <div class="animal-card">
      <v-card class="ma-6" max-width="344">
        <v-img :src="fotoAnimal" height="200px"></v-img>
        <v-card-title>{{ nombre }}</v-card-title>
        <v-card-subtitle>{{ especie }}, {{ edad }}</v-card-subtitle>
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
            <v-card-text>{{ descripcion }}</v-card-text>
          </div>
        </v-expand-transition>
      </v-card>
  </div>
</template>

<script>
export default {
    data(){
        return{
            fotoAnimal:'https://images4.alphacoders.com/101/thumb-350-1016550.jpg',
            nombre:'Pumba',
            especie:'jabalí',
            edad:'8 años',
            show: false,
            descripcion:'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vitae libero efficitur, ullamcorper tellus ut, feugiat arcu. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vivamus accumsan pellentesque ante, et ullamcorper arcu. Proin nibh sapien, hendrerit sit amet ex a, posuere viverra elit. Mauris varius faucibus diam, id vestibulum velit imperdiet quis. Pellentesque habitant morbi.',
        }
    }
}
</script>