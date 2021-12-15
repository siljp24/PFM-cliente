<template>
    <div class="crear-animal">
        <v-form>
            <v-card>
                <v-card-title class="justify-center">CREAR ANIMAL</v-card-title>
                <v-card-text>
                    <v-file-input v-model="perfilAnimal" placeholder="Foto" required></v-file-input>
                    <v-text-field v-model="nombre" placeholder="Nombre" required></v-text-field>
                    <v-text-field v-model="edad" placeholder="Edad" required></v-text-field>
                    <v-textarea v-model="descripcion" placeholder="Descripcion" required></v-textarea>
                    <v-text-field v-model="especie" placeholder="Especie" required></v-text-field>
                </v-card-text>
                <v-btn block elevation="2" v-on:click="onSubmit"> CREAR</v-btn>
            </v-card>
        </v-form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            perfilAnimal: '',
            nombre:'',
            edad:'',
            descripcion:'',
            especie:'',
        }
    },
    methods:{
        async onSubmit(){
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
                const res = await fetch('http://localhost:4500/api/animal/crearAnimal',{
                    method:'post',
                    headers:{
                        token:token,
                    },
                    body: formData,
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                }
                this.$router.push('/voluntario/main');
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>