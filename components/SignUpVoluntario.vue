<template>
    <div class="sign-up-voluntario">
         <v-form ref="form" v-model="valid" >
                <v-card>
                    <v-card-title class="subtitulo justify-center">Registrarme</v-card-title>
                    <v-card-text>
                        <v-text-field v-model="nombre" placeholder="Nombre (más de 3 caracteres)" required></v-text-field>
                        <v-text-field v-model="email" placeholder="Email" required type="email"></v-text-field>
                        <v-text-field v-model="password" required placeholder="Contraseña (más de 5 caracteres)" type="password"></v-text-field>
                        <v-text-field v-model="password2" required placeholder="Repetir contraseña" type="password"></v-text-field>
                        <v-checkbox v-model="condiciones" label="Acepto las condiciones" required :rules="[v => !!v ||'Debes aceptar condiciones para continuar']"></v-checkbox>
                        <v-btn block v-on:click="onSubmit">Enviar</v-btn>
                    </v-card-text>
                </v-card>    
        </v-form>  
    </div>
</template>

<script>
export default {
    data(){
        return{
            valid:true,
            nombre:'',
            email:'',
            password:'',
            password2:'',
            condiciones:false,
        }
    },
    methods:{
        // validate(){
        //    this.$refs.form.validate()
        // },
        async onSubmit(){ 
            this.$refs.form.validate()
             if(this.password !== this.password2 ){
                alert("Las contraseñas son diferentes");
                return;
            };
            if(this.password.length <= 5 || this.password2.length <= 5){
                alert("Las contraseñas son demasiado cortas");
                return;
            };
            if(this.nombre.length <= 3){
                alert("nombre demasiado corto");
                return;
            };
            if(!this.email.includes("@")){
                alert("introduzca un email");
            };
            try{
                const body = JSON.stringify({
                    email: this.email,
                    nombre: this.nombre,
                    clave: this.password,
                });
                const res = await fetch('http://localhost:4500/api/voluntario/crearVoluntario',{
                    method: 'post',
                    headers:{
                        'Content-Type': 'application/json',
                    },
                    body,
                });
                const data = await res.json();
                console.log(data)
                if(data.error){
                    alert(data.error);
                    return;
                }else{
                    this.$router.push('/voluntario/sesion');
                }
            }catch(err){
                console.log(err);
            }

        }
    }
}
</script>