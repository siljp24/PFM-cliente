<template>
    <div class="perfil-voluntario">
         <v-row>
            <v-col cols="5">
                <FotoPerfil />
            </v-col>
            <v-col cols="7">
                <UpdateVoluntario :perfil="perfil"/>
            </v-col>
        </v-row>
    </div>
</template>

<script>
export default {
     layout:'perfil',
    data(){
        return{
            perfil:{
                nombre:'',
                direccion:'',
                telefono:''
            },
        }
    },
    async beforeMount(){
        await this.cargarPerfil();
    },
    methods:{
        async cargarPerfil(){
            try{
                const token = window.localStorage.getItem('token');
                const res = await fetch('http://localhost:4500/api/voluntario/obtenerVoluntario',{
                    headers:{
                        token,
                    },
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                };
                this.perfil = data.voluntario;
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>
