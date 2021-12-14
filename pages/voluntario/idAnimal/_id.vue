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
                <DiarioCard :diario="diario"/>
            </div>
        </v-row>
       
    </div>
</template>

<script>
export default {
    layout: 'animal',
    data(){
        return{
            diarios:[],
        }
    },
    async beforeMount(){
        await this.loadDiaries();
    },
    methods:{
        async loadDiaries(){
             try{
                const idAnimal = this.$route.params.id;
                const res = await fetch(`http://localhost:4500/api/diario/diariosAnimal/${idAnimal}`,
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
                    const diarios = data.diarios;
                    for(let i = 0; i < diarios.length; i++){
                    this.diarios.push(diarios[i]);
                    }
                };
            }catch(err){
            console.log(err);
        }
        }
    }
}
</script>