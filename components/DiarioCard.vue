<template>
    <div class="diario-animal">
        <v-card elevation="12" class="ma-5" min-width="344" max-width="344">
           <v-img class="white--text align-end" height="200px" :src="diario.foto" v-on:click="leerHistoria(diario._id)"></v-img> 
           <v-card-subtitle class="pb-0 text-center">{{ diario.fecha}}</v-card-subtitle>
           <v-card-actions>
                <v-dialog v-model="dialog" width="500">
                        <template v-slot:activator="{ on, attrs }">
                             <v-btn color="orange" text v-bind="attrs" v-on="on">Eliminar</v-btn>
                        </template>
                        <v-card>
                            <v-card-title class="text-h5 grey lighten-2"></v-card-title>
                            <v-card-text>
                            ¿Estás seguro de eliminar esta historia?
                            </v-card-text>
                            <v-divider></v-divider>
                            <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="primary" text @click="dialog = false">NO</v-btn>
                            <v-btn color="primary" text @click="dialog = false" v-on:click="eliminarDiario(diario._id, diario.idAnimal)">SÍ</v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-dialog>
                <v-spacer></v-spacer>
                <v-btn color="teal darken-4" text @click="irAnadirHistoria(diario._id, diario.idAnimal)">Editar</v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
export default {
    props:{
        diario:{
            type:Object,
            required:true,
        }
    },
    data(){
        return{
            dialog: false,
        }
    },
    methods:{
        leerHistoria(idHistoria){
            this.$router.push(`/voluntario/idHistoria/${idHistoria}`);
        },
        irAnadirHistoria(idDiario, idAnimal){
            localStorage.setItem('idDiario', idDiario);
            localStorage.setItem('idAnimal', idAnimal);
            this.$router.push("/voluntario/idHistoria/editar");
        },
        async eliminarDiario(idDiario, idAnimal){
            try{
                const token = localStorage.getItem('token');
                const body = JSON.stringify({
                    idDiario,
                    idAnimal,
                });
                const res = await fetch('http://localhost:4500/api/diario/eliminarDiario',{
                    method: 'delete',
                    headers:{
                        'Content-Type': 'application/json',
                        token,
                    },
                    body,
                    
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                };
                this.$emit('onUpdateDiaries');
            }catch(err){
                console.log(err);
            }
        }
    }
    
}
</script>