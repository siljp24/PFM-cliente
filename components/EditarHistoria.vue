<template>
    <div class="editar-historia">
        <v-form>
            <v-card>
                <v-card-title class="justify-center"> HISTORIA</v-card-title>
                <v-card-text>
                    <v-file-input v-model="diarioAnimal" placeholder="Foto"></v-file-input>
                    <v-menu ref="menu" v-model="menu" :close-on-content-click="false" :return-value.sync="date" transition="scale-transition" offset-y min-width="auto"
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-text-field v-model="date" label="Fecha" prepend-icon="mdi-calendar" readonly v-bind="attrs" v-on="on"
                            ></v-text-field>
                        </template>
                        <v-date-picker v-model="date" no-title scrollable>
                            <v-spacer></v-spacer>
                            <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
                            <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
                        </v-date-picker>
                    </v-menu>
                    <v-textarea v-model="descripcion" placeholder="Suceso" required></v-textarea>
                </v-card-text>
                <v-btn block v-on:click="onSubmit" elevation="2"> ENVIAR</v-btn>
            </v-card>
        </v-form> 
    </div>
</template>

<script>
export default {
    data(){
        return{
            date:(new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            diarioAnimal: '',
            descripcion:'',
            menu: false,
        }
    },
    methods:{
        async onSubmit(){
        console.log("entramos")
            if(this.date.length === 0 || this.diarioAnimal.length === 0 || this.descripcion.length === 0){
                alert("Todos los campos deben ser completados");
                return;
            };
            try{
                const idDiario = localStorage.getItem('idDiario');
                console.log({idDiario})
                const token = localStorage.getItem('token');
                console.log({token})
                const idAnimal = localStorage.getItem('idAnimal');
                const formData = new FormData();
                formData.enctype = 'multipart/form-data';
                formData.append('diarioAnimal', this.diarioAnimal);
                formData.append('descripcion', this.descripcion);
                formData.append('fecha', this.date);
                formData.append('idAnimal', idAnimal);
                const res = await fetch(`http://localhost:4500/api/diario/editarDiario/${idDiario}`,{
                    method:'put',
                    headers:{
                        token:token,
                    },
                    body: formData,
                });
                const data = await res.json();
                console.log({ data })
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