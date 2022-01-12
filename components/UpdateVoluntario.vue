<template>
    <div class="update-voluntario">
         <v-form ref="form" lazy-validation class="mb-6">
                <v-card>
                    <v-card-title class="subtitulo justify-center">Mis datos</v-card-title>
                    <v-card-text>
                        <v-text-field v-model="perfil.nombre" required type="text"></v-text-field>
                        <v-text-field v-model="perfil.direccion" required type="text" prepend-inner-icon="mdi-map-marker"></v-text-field>
                        <v-text-field v-model="perfil.telefono" required type="number"></v-text-field>
                        <v-text-field v-model="password" required placeholder="Contraseña (más de 5 caracteres)" type="password"></v-text-field>
                        <v-text-field v-model="password2" required placeholder="Repetir contraseña" type="password"></v-text-field>
                        <v-btn block @click="validate">Enviar</v-btn>
                    </v-card-text>
                </v-card>    
        </v-form>
        <v-dialog v-model="dialog" width="500">
            <template v-slot:activator="{ on, attrs }">
                <p>¿Deseas darte de baja como voluntario? <a v-bind="attrs" v-on="on">Darme de baja</a></p>
            </template>
            <v-card>
                <v-card-title class="text-h5">Baja como voluntario</v-card-title>
                <v-card-text>¿Estás seguro de darte de baja como voluntario de la reserva? Tus datos se eliminarán para siempre</v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="green darken-1" text @click="dialog = false">NO</v-btn>
                    <v-btn color="green darken-1" text @click="dialog = false">SÍ</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </div>
</template>

<script>
export default {
    props:{
        perfil:{
            type:Object,
            required:true,
        }
    },
    data(){
        return{
            password:'',
            password2:'',
            dialog: false,
        }
    },
    methods:{
        async validate(){ 
             if(this.password !== this.password2 ){
                alert("Las contraseñas son diferentes");
                return;
            };
            if(this.password.length <= 5 || this.password2.length <= 5){
                alert("Las contraseñas son demasiado cortas");
                return;
            };
            if(this.$props.perfil.nombre.length <= 3){
                alert("nombre demasiado corto");
                return;
            };
             if(this.$props.perfil.telefono < 999999999 && this.$props.perfil.telefono >= 111111111){
                alert("telefono incorrecto");
                return;
            };
            try{
                const body = JSON.stringify({
                    email: this.$props.perfil.email,
                    direccion: this.$props.perfil.direccion,
                    nombre: this.$props.perfil.nombre,
                    telefono: this.$props.perfil.telefono,
                    clave: this.password,
                });
                const res = await fetch('http://localhost:4500/api/voluntario/actualizarVoluntario',{
                    method: 'put',
                    headers:{
                        'Content-Type': 'application/json',
                    },
                    body,
                });
                const data = await res.json();
                if(data.error){
                    alert(data.error);
                    return;
                }else{
                    this.$router.push('/voluntario/main');
                }
            }catch(err){
                console.log(err);
            }

        }
    }
}
</script>