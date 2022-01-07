<template>
    <div class="update-voluntario">
         <v-form ref="form" v-model="valid" lazy-validation class="mb-6">
                <v-card>
                    <v-card-title class="subtitulo justify-center">Mis datos</v-card-title>
                    <v-card-text>
                        <v-text-field v-model="nombre" placeholder="Nombre (más de 3 caracteres)" required></v-text-field>
                        <v-text-field v-model="direccion" placeholder="Dirección" required type="text" prepend-inner-icon="mdi-map-marker"></v-text-field>
                        <v-text-field v-model="telefono" placeholder="Teléfono" required type="number"></v-text-field>
                        <v-text-field v-model="password" required placeholder="Contraseña (más de 5 caracteres)" type="password"></v-text-field>
                        <v-text-field v-model="password2" required placeholder="Repetir contraseña" type="password"></v-text-field>
                        <v-btn block @click="validate">Enviar</v-btn>
                    </v-card-text>
                </v-card>    
        </v-form>  
    </div>
</template>