<template>
    <div class="editar-animal">
         <v-form>
            <v-card>
                <v-card-title class="justify-center">EDITAR ANIMAL</v-card-title>
                <v-card-text>
                    <v-file-input v-model="foto" placeholder="Foto" required></v-file-input>
                    <v-text-field v-model="nombre" placeholder="Nombre" required></v-text-field>
                    <v-text-field v-model="edad" placeholder="Edad" required></v-text-field>
                    <v-textarea v-model="descripcion" placeholder="Descripcion" required></v-textarea>
                    <v-text-field v-model="especie" placeholder="Especie" required></v-text-field>
                </v-card-text>
            </v-card>
            <v-row class="mt-8">
                <v-col cols="6">
                    <v-dialog v-model="dialog" width="500">
                        <template v-slot:activator="{ on, attrs }">
                            <v-btn color="red lighten-2" dark v-bind="attrs" v-on="on">ELIMINAR</v-btn>
                        </template>
                        <v-card>
                            <v-card-title class="text-h5 grey lighten-2"></v-card-title>
                            <v-card-text>
                            ¿Estás seguro de eliminar este animal?
                            </v-card-text>
                            <v-divider></v-divider>
                            <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="primary" text @click="dialog = false">NO</v-btn>
                            <v-btn color="primary" text @click="dialog = false">SÍ</v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-dialog>
                </v-col>
                <v-col cols="6">
                    <v-btn disabled elevation="2" block> EDITAR</v-btn>
                </v-col>
            </v-row>
        </v-form>
    </div>
</template>
<script>
export default {
    data(){
        return{
            foto: undefined,
            nombre: '',
            edad: '',
            descripcion:'',
            especie:'',
            justify:[
                'start',
                'end',
            ],
            dialog: false,
        }
    }
}
</script>