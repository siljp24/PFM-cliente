<template>
    <div class="editar-animal">
         <v-form>
            <v-card>
                <v-card-title class="justify-center">EDITAR ANIMAL</v-card-title>
                <v-card-text>
                    <v-file-input v-model="perfilAnimal" placeholder="Foto" required></v-file-input>
                    <v-text-field v-model="animal.nombre" placeholder="Nombre" required></v-text-field>
                    <v-text-field v-model="animal.edad" type="number" placeholder="Edad" required></v-text-field>
                    <v-textarea v-model="animal.descripcion" placeholder="Descripcion" required></v-textarea>
                    <v-text-field v-model="animal.especie" placeholder="Especie" required></v-text-field>
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
                            <v-btn color="primary" text @click="dialog = false" v-on:click="eliminarAnimal">SÍ</v-btn>
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
    props:{
        animal:{
            type: Object,
            required:true,
        },
    },
    data(){
        return{
            perfilAnimal: undefined,
            justify:[
                'start',
                'end',
            ],
            dialog: false,
        }
    },
    methods:{
        async edit(){
            if(this.$props.animal.nombre.length === 0 ||this.$props.animal.edad.length === 0 || this.$props.animal.descripcion.length === 0 || this.$props.animal.especie.length === 0){
                alert("Es necesario rellenar todos los campos");
                return;
            };
            if(this.perfilAnimal !== undefined && this.perfilAnimal.length >= 1000000){
                alert("Foto demasiado grande");
                return;
            }
            try{
                const idAnimal = this.$route.params.id
                const formData = new FormData();
                formData.enctype = 'multipart/form-data';
                if(this.perfilAnimal !== undefined){
                    formData.append('perfilAnimal', this.perfilAnimal);
                }
                formData.append('nombre', this.$props.animal.nombre);
                formData.append('especie', this.$props.animal.especie);
                formData.append('descripcion', this.$props.animal.descripcion);
                formData.append('edad', this.$props.animal.edad);
                const token = localStorage.getItem('token');
                const res = await fetch(`http://localhost:4500/api/animal/editarAnimal/${idAnimal}`,{
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
                this.$router.push(`/voluntario/idAnimal/${idAnimal}`);
            }catch(err){
                console.log(err);
            }
        },
        async eliminarAnimal(){
            try{
                const idAnimal = this.$route.params.id;
                const token = localStorage.getItem('token');
                const body = JSON.stringify({idAnimal});
                const res = await fetch('http://localhost:4500/api/animal/eliminarAnimal',{
                    method:'delete',
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
                this.$router.push('/voluntario/main');
            }catch(err){
                console.log(err);
            }
        },
    }
}
</script>