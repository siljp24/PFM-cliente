<template>
    <div class="voluntario-editar-animal">
        <v-row>
            <v-col cols="2">
                <v-btn v-on:click="toBack" block color="deep-orange lighten-3">VOLVER</v-btn>
            </v-col>
        </v-row>
         <v-row>
            <v-col md="6" offset-md="3">
                <EditarAnimal :animal="animal"/>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
    layout: 'crearEditarAnimal',
   data(){
        return{
           animal:{},
        }
    },
    async beforeMount(){
        await this.getAnimal();
    },
    methods:{
        async getAnimal(){
            const idAnimal = this.$route.params.id;
            const res = await fetch(`http://localhost:4500/api/animal/${idAnimal}`);
            const data = await res.json();
            if(data.error){
                alert(data.error);
                return;
            }
            this.animal = data.animal;
        },
        toBack(){
            this.$router.push(`/voluntario/idAnimal/${this.$route.params.id}`)
        }
    }
    
}
</script>


