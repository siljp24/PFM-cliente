<template>
    <div class="crear-animal">
        <v-form>
            <v-card>
                <v-card-title class="justify-center">CREAR ANIMAL</v-card-title>
                <v-card-text>
                    <v-file-input v-model="foto" placeholder="Foto" required></v-file-input>
                    <v-text-field v-model="nombre" placeholder="Nombre" required></v-text-field>
                    <v-text-field v-model="edad" placeholder="Edad" required></v-text-field>
                    <v-textarea v-model="descripcion" placeholder="Descripcion" required></v-textarea>
                    <v-text-field v-model="especie" placeholder="Especie" required></v-text-field>
                </v-card-text>
                <v-btn block  disabled elevation="2"> CREAR</v-btn>
            </v-card>
        </v-form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            foto: undefined,
            nombre:'',
            edad:'',
            descripcion:'',
            especie:'',
        }
    }
}
</script>