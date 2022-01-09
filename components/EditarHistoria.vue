<template>
    <div class="editar-historia">
        <v-form>
            <v-card>
                <v-card-title class="justify-center"> HISTORIA</v-card-title>
                <v-card-text>
                    <v-file-input v-model="diarioAnimal" placeholder="Foto"></v-file-input>
                    <v-menu ref="menu" v-model="menu" :close-on-content-click="false" :return-value.sync="diario.fecha" transition="scale-transition" offset-y min-width="auto"
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-text-field v-model="diario.fecha" label="Fecha" prepend-icon="mdi-calendar" readonly v-bind="attrs" v-on="on"
                            ></v-text-field>
                        </template>
                        <v-date-picker v-model="diario.fecha" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                            <v-btn text color="primary" @click="$refs.menu.save(diario.fecha)">OK</v-btn>
                        </v-date-picker>
                    </v-menu>
                    <v-textarea v-model="diario.descripcion" placeholder="Suceso" required></v-textarea>
                </v-card-text>
                <v-btn block v-on:click="onSubmit" elevation="2"> ENVIAR</v-btn>
            </v-card>
        </v-form> 
    </div>
</template>

<script>
export default {
    props:{
        diario:{
            type: Object,
            required: true,
        }
    },
    data(){
        return{
            diarioAnimal: undefined,
            menu: false,
        }
    },
    methods:{
        async onSubmit(){
            if(this.$props.diario.fecha === undefined || this.$props.diario.descripcion.length === 0){
                alert("Todos los campos deben ser completados");
                return;
            };
            if(this.diarioAnimal !== undefined && this.diarioAnimal.length >= 1000000){
                alert("Foto demasiado grande");
                return;
            }
            try{
                const idDiario = this.$props.diario._id;
                const token = localStorage.getItem('token');
                const idAnimal = this.$props.diario.idAnimal;
                const formData = new FormData();
                formData.enctype = 'multipart/form-data';
                formData.append('diarioAnimal', this.diarioAnimal);
                formData.append('descripcion', this.$props.diario.descripcion);
                formData.append('fecha', this.$props.diario.fecha);
                formData.append('idAnimal', idAnimal);
                const res = await fetch(`http://localhost:4500/api/diario/editarDiario/${idDiario}`,{
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
                }
                this.$router.push(`/voluntario/idAnimal/${idAnimal}`);
                localStorage.removeItem('idDiario');
                localStorage.removeItem('idAnimal');
            }catch(err){
                console.log(err);
            }
        }
    }
    }
    
</script>