<template>
  <div class="index">
    <v-row>
      <div v-for="(animal,index) in animales" :key="index">
        <AnimalCard :animal="animal"/>
      </div>
    </v-row>
  </div>
</template>

<script>
export default {
  data(){
    return{
      animales:[],
    }
  },
  async beforeMount(){
    console.log("beforemount")
    await this.loadAnimals();
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
        console.log(res)
        const data = await res.json();
        console.log(data)
        if(data.error){
          alert(data.error);
        }else{
        const animales = data.animales;
        console.log(animales)
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
