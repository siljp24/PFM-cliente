<template>
    <div class="voluntario-idHistoria-editar">
        <v-row>
            <v-col cols="2">
                <v-btn v-on:click="toBack" block color="deep-orange lighten-3">DIARIO</v-btn>
            </v-col>
            <v-col cols="10"></v-col>
        </v-row>
        <v-row>
            <v-col md="6" offset-md="3"><EditarHistoria :diario="diario"/></v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    layout:'crearEditarHistoria',
    data(){
        return{
            diario:{},
        }
    },
    async beforeMount(){
        await this.getHistory();
    },
    methods:{
        toBack(){
            const idAnimal = localStorage.getItem('idAnimal');
            this.$router.push(`/voluntario/idAnimal/${idAnimal}`);
            localStorage.removeItem('idAnimal');
            localStorage.removeItem('idDiario');
        },
        async getHistory(){
            try{
                const idDiario = localStorage.getItem('idDiario');
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
                };
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>