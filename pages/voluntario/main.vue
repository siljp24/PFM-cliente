<template>
    <div class="voluntarios-main">
        <v-row>
            <v-col cols="12" v-if="token">
                <v-flex text-right>
                    <v-btn color="green lighten-2" v-on:click="toCreateAniaml">NUEVO ANIMAL</v-btn>
                </v-flex>
            </v-col>
        </v-row>
        <v-row>
            <div v-for="(animal,index) in animales" :key="index">
            <AnimalCard :animal="animal"/>
        </div>
        </v-row>
          <Footer />
    </div>
</template>

<script>
export default {
    layout:'mainVoluntarios',
     data(){
        return{
          animales:[],
          token:undefined,
        }
  },
  async beforeMount(){
    await this.loadAnimals();
  },
  mounted(){
    const token = window.localStorage.getItem('token');
    this.token = token;
  },
  methods:{
    async loadAnimals(){
      try{
        const res = await fetch('https://reservanimal.herokuapp.com/api/animal/listaAnimales',
        {
            headers: {
              'Content-Type': 'application/json',
            }
        }
        );
        const data = await res.json();
        if(data.error){
          alert(data.error);
        }else{
        const animales = data.animales;
        for(let i = 0; i < animales.length; i++){
          this.animales.push(animales[i]);
        }
        };
      }catch(err){
        console.log(err);
      }
    },
    toCreateAniaml(){
        this.$router.push('/voluntario/crearAnimal');
    }
  }
}
</script>