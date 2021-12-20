<template>
    <div class="editar-animal">
         <v-form>
            <v-card>
                <v-card-title class="justify-center">EDITAR ANIMAL</v-card-title>
                <v-card-text>
                    <v-file-input v-model="perfilAnimal" placeholder="Foto" required></v-file-input>
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
                    <v-btn elevation="2" block v-on:click="edit"> EDITAR</v-btn>
                </v-col>
            </v-row>
        </v-form>
    </div>
</template>
<script>
export default {
    data(){
        return{
            perfilAnimal: '',
            nombre: '',
            edad: '',
            descripcion:'',
            especie:'',
            justify:[
                'start',
                'end',
            ],
            dialog: false,
            idAnimal:this.$route.params.id,
        }
    },
    methods:{
        async edit(){
            if(this.nombre.length === 0 ||this.edad.length === 0 || this.descripcion.length === 0 || this.especie.length === 0 || this.perfilAnimal.length === 0){
                alert("Es necesario rellenar todos los campos");
                return;
            };
            try{
                const formData = new FormData();
                formData.enctype = 'multipart/form-data';
                formData.append('perfilAnimal', this.perfilAnimal);
                formData.append('nombre', this.nombre);
                formData.append('especie', this.especie);
                formData.append('descripcion', this.descripcion);
                formData.append('edad', this.edad);
                const token = localStorage.getItem('token');
                const res = await fetch(`http://localhost:4500/api/animal/editarAnimal/${this.idAnimal}`,{
                    method:'put',
                    headers:{
                        token:token,
                    },
                    body: formData,
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                };
                this.$router.push(`/voluntario/idAnimal/${this.idAnimal}`);
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>