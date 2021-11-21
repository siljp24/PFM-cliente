<template>
  <div class="index">
    <v-row>
      <div v-for="(animal,index) in animales" :key="index">
        <AnimalCard />
      </div>
    </v-row>
  </div>
</template>

<script>
export default {
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
