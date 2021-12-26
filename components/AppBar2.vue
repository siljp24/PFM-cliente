<template>
    <div class="app-bar">
            <v-card>
                <v-app-bar color="brown" dark>
                    <div v-if="token" >
                        <v-btn plain to="/voluntario/main" style="position:relative;left:0;"><v-toolbar-title> LA RESERVA</v-toolbar-title></v-btn>
                        <v-btn class="mr-2 brown lighten-1" style="position:absolute;right:0;" v-on:click="logout">Cerrar Sesión</v-btn>
                    </div>
                    <div v-else>
                        <v-btn plain to="/" style="position:relative;left:0;"><v-toolbar-title> LA RESERVA</v-toolbar-title></v-btn>
                        <v-btn class="mr-2 brown lighten-1" to="/voluntario/sesion" style="position:absolute;right:0;">Área voluntariado</v-btn>
                    </div>
                </v-app-bar>
            </v-card>
       
    </div>
</template>

<script>
  export default {
    data(){
        return{
            token:'',
        }
    },
    mounted(){
        this.token = window.localStorage.getItem('token');
    },
    methods:{
        logout(){
            this.$router.push('/');
            window.localStorage.clear();
        }
    }
  }
</script>