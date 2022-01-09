<template>
    <div class="app-bar">
            <v-card>
                <v-app-bar color="brown" dark>
                    <v-row v-if="token">
                        <v-col cols="8" class="mt-1">
                        <v-btn plain to="/voluntario/main"><v-toolbar-title> LA RESERVA</v-toolbar-title></v-btn>
                    </v-col>
                    <v-col cols="4" class="text-right">
                        <v-btn color="green accent-4" dark fab plain v-on:click="toProfile"><v-icon large>mdi-account</v-icon></v-btn>
                        <v-btn class=" brown lighten-1 ms-2" v-on:click="logout" plain>Cerrar Sesión</v-btn>
                    </v-col>
                </v-row>
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
        },
        toProfile(){
            this.$router.push('/voluntario/perfil');
        }
    }
  }
</script>