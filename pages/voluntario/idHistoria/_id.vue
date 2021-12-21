<template>
    <div class="voluntario-idHistoria">
        <v-row class="mt-10">
            <v-col cols="2">
                <v-btn v-on:click="goBack" block color="deep-orange lighten-3">DIARIO</v-btn>
            </v-col>
        </v-row>
        <v-row class="mt-10">
            <v-col class="mt-10">
                <Historia :diario="diario"/>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    layout:'historiaAnimal',
    data(){
        return{
            diario:{},
            idAnimal:'',
        }
    },
    async beforeMount(){
        await this.loadHistory();
    },
    methods:{
        async loadHistory(){
             try{
                const idDiario = this.$route.params.id;
                const res = await fetch(`http://localhost:4500/api/diario/${idDiario}`,
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
                    this.diario = data.diario;
                    this.idAnimal = data.diario.idAnimal;
                };
            }catch(err){
                console.log(err);
            }
        }, 
        goBack(){
            this.$router.push(`/voluntario/idAnimal/${this.idAnimal}`);
        }
    }
}
</script>