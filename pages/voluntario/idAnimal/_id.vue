<template>
    <div class="voluntario-idAnimal">
        <v-row  v-if="token">
            <v-col class="text-start">
                <v-btn color="orange lighten-2" v-on:click="toEditAnimal" class="mr-6">EDITAR ANIMAL</v-btn>
                <v-btn color="green lighten-2" v-on:click="toNewHistory">Nueva historia</v-btn>
            </v-col>
        </v-row>
        <v-row>
            <div v-for="(diario,index) in diarios" :key="index">
                <DiarioCard :diario="diario" @onUpdateDiaries="handleUpdates"/>
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
            idAnimal:this.$route.params.id,
            token:'',
        }
    },
    async beforeMount(){
        await this.loadDiaries();
        this.token = window.localStorage.getItem('token');
    },
    methods:{
        async loadDiaries(){
             try{
                const res = await fetch(`https://reservanimal.herokuapp.com/api/diario/diariosAnimal/${this.idAnimal}`,
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
        },
        toEditAnimal(){
            this.$router.push(`/voluntario/idAnimal/editarAnimal/${this.idAnimal}`);
        },
        toNewHistory(){
            localStorage.setItem("idAnimal", this.idAnimal);
            this.$router.push("/voluntario/anadirHistoria");
        },
        async handleUpdates(){
            this.diarios=[];
            await this.loadDiaries();
        }
    }
}
</script>