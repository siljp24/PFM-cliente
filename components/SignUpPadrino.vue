<template>
    <div class="sign-up-padrino">
          <v-form ref="form" v-model="valid" >
                <v-card>
                    <v-card-title class="subtitulo justify-center">Registrarme</v-card-title>
                    <v-card-text>
                        <v-text-field v-model="nombre" placeholder="Nombre" required></v-text-field>
                        <v-text-field v-model="email" placeholder="Email" required type="email"></v-text-field>
                        <v-text-field v-model="contraseña" required placeholder="Contraseña" type="password"></v-text-field>
                        <v-text-field v-model="contraseña2" required placeholder="Repetir contraseña" type="password"></v-text-field>
                        <v-text-field v-model="cuentaBancaria" required placeholder="Nº de cuenta"></v-text-field>
                        <v-checkbox v-model="condiciones" label="Acepto las condiciones" required :rules="[v => !!v ||'Debes aceptar condiciones para continuar']"></v-checkbox>
                        <v-btn block @click="validate" to="/padrino/sesion">Enviar</v-btn>
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
            contraseña:'',
            contraseña2:'',
            cuentaBancaria:'',
            condiciones:false,
        }
    },
    methods:{
        validate(){
            this.$refs.form.validate()
        }
    }
}
</script>