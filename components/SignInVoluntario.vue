<template>
    <div class="sign-in-voluntario">
        <v-form>
            <v-card>
                <v-card-title class="subtitulo justify-center">
                    Iniciar Sesión 
                </v-card-title>
                <v-card-text>
                    <v-text-field v-model="email" required placeholder="Email" type="email"></v-text-field>
                    <v-text-field v-model="password" required placeholder="Contraseña" type="password"></v-text-field>
                    <v-btn block class="brown lighten-4" v-on:click="onSubmit"> Entrar</v-btn>
                </v-card-text>
            </v-card>
        </v-form>
        <p class="mt-2">¿Aún no tienes cuenta? <a href="/voluntario/registro">Registrarme</a></p>
    </div>
</template>

<script>
export default {
    data(){
        return{
            email:'',
            password:'',
        }
    },
    methods:{
        async onSubmit(){
            try{
                const body = JSON.stringify({
                    email: this.email,
                    clave: this.password,
                });
                const res = await fetch('https://reservanimal.herokuapp.com/api/voluntario/identificarVoluntario',{
                    method:'post',
                    headers:{
                        'Content-Type': 'application/json',
                    },
                    body,
                });
                const data = await res.json();
                console.log({data})
                if(data.error){
                    alert(data.error);
                    return;
                }else{
                    window.localStorage.setItem('token', data.token);
                    this.$router.push('/voluntario/main');
                }
            }catch(err){
                console.log(err);
            }
        }
    }
}
</script>