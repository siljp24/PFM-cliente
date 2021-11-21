<template>
    <div class="sign-in-voluntario">
        <v-form>
            <v-card>
                <v-card-title class="subtitulo justify-center">
                    Iniciar Sesión 
                </v-card-title>
                <v-card-text>
                    <v-text-field v-model="email" required placeholder="Email" type="email"></v-text-field>
                    <v-text-field v-model="contraseña" required placeholder="Contraseña" type="password"></v-text-field>
                    <v-btn block class="brown lighten-4" to="/voluntario/main"> Entrar</v-btn>
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
            contraseña:'',
        }
    }
}
</script>