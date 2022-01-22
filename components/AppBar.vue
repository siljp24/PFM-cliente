<template>
    <div class="app-bar">
        <v-card>
            <v-app-bar color="brown" dark class="appBar">
                <v-row v-if="token">
                    <v-col cols="8" class="mt-1">
                        <v-btn class="reserva" plain to="/voluntario/main"><v-toolbar-title> LA RESERVA</v-toolbar-title></v-btn>
                    </v-col>
                    <v-col cols="4" class="text-right logueo">
                        <v-btn color="green accent-4" dark fab plain v-on:click="toProfile"><v-icon large>mdi-account</v-icon></v-btn>
                        <v-btn color=" white lighten-1 ms-2" v-on:click="logout" plain> LOGOUT <v-icon>mdi-logout</v-icon></v-btn>
                    </v-col>
                </v-row>
                <div v-else>
                    <v-btn plain to="/" class="reserva" style="position:relative;left:0;"><v-toolbar-title> LA RESERVA</v-toolbar-title></v-btn>
                    <v-btn class="mr-2 brown lighten-1 btnLoguin" to="/voluntario/sesion" style="position:absolute;right:0;">Área voluntariado</v-btn>
                </div>
            </v-app-bar>
            <v-img :src="require('../assets/bosque.png')" height="400px"/>
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

<style scoped>
@media (max-width:615px){
    .reserva{
        width: 100%;
        display: inline;
    }
    .logueo{
        width: 100%;
        display: inline;
        height: 100%;
        margin-top: 10px;
    }
    .appBar{
        min-height: 83px;
        width: 100%;
       display: inline-flex; 
    }
    .btnLoguin{
        position: fixed;
        right: 0;
        left: 0;
        width: 120%;
        margin-left: 20px;
      
    }
}
</style>