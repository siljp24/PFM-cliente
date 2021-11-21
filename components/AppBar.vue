<template>
    <div class="app-bar">
        <v-card>
            <v-app-bar
            color="brown"
            dark
            >
                <v-btn plain to="/"><v-toolbar-title> LA RESERVA</v-toolbar-title></v-btn>
                <v-spacer></v-spacer>
                <v-btn class="mr-2 brown lighten-1" to="/voluntario/sesion">Área voluntariado</v-btn>
                <v-btn class="brown lighten-1" to="/padrino/sesion">Área de padrinos</v-btn>
            </v-app-bar>
            <v-img :src="bosque" height="400px"/>
        </v-card>
    </div>
</template>

<script>
  export default {
    data(){
        return{
            bosque:"https://www.fundacionaquae.org/wp-content/uploads/2019/11/pregunta1.jpg",
        }
    }
  }
</script>