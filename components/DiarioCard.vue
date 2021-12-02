<template>
    <div class="diario-animal">
        <v-card elevation="12" class="ma-5" max-width="350">
           <v-img class="white--text align-end" height="200px" :src="diario.foto" v-on:click="leerHistoria"></v-img> 
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
                            <v-btn color="primary" text @click="dialog = false">SÍ</v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-dialog>
                <v-spacer></v-spacer>
                <v-btn color="teal darken-4" text v-bind="attrs" v-on="on" @click="irAnadirHistoria">Editar</v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
export default {
    data(){
        return{
            diario:{
                foto:'https://upload.wikimedia.org/wikipedia/commons/7/76/Atr3e.jpg',
                fecha:'YY/YY/YYYY',
            },
            dialog: false,
        }
    },
    methods:{
        leerHistoria(){
            this.$router.push('/voluntario/idHistoria');
        },
        irAnadirHistoria(){
            this.$router.push("/voluntario/idHistoria/editar");
        }
    }
    
}
</script>