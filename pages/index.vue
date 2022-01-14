<template>
  <div class="index" v-if="!token">
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
    this.$router.push('/voluntario/main');
  },
  methods:{
    async loadAnimals(){
      try{
        const res = await fetch('http://localhost:4500/api/animal/listaAnimales',
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
    }
  }
}
</script>
